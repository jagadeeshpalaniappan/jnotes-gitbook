# One to Many Relationship



With the difference based on the quantity, we can distinguish between **Three types of One-to-Many relationships:** \( E.g. Tutorial Blog App\)

* **One-to-Few**
  * **E.g**. A Tutorial has some Images \(15 or less\)
  * **Design:** Embedded Data Models
* **One-to-Many**
  * **E.g.** A Tutorial has many Comments
  * **Design:**  Embedded/Reference Data Models
    * **Data Access Patterns:** decide based on "read/write" ratio
    * If the collections is mostly read and the data is not updated a lot, then we consider embedding the data.
    * If the collections data is updated a lot then we should consider referencing \(normalizing\) the data. That’s because the database engine does more work to update and embed a document than a standalone document
* **One-to-aLot**
  * **E.g.** A Category has a lot of Tutorials
  * **Design:** Reference Data Models

Depending on the "**types of relationships**", on "**data access patterns**", or on "**data cohesion**", we will decide how to implement the data model, in other words, decide if we should denormalize or normalize data.

**Data Access Patterns:** decide based on "read/write" ratio 

* If the collections is mostly read and the data is not updated a lot, then we consider embedding the data. 
* If the collections data is updated a lot then we should consider referencing \(normalizing\) the data. That’s because the database engine does more work to update and embed a document than a standalone document

**Data cohesion:** how much the data is related.

* If two collections really intrinsically belong together then they should probably be embedded into one another. In our example, all Tutorials can have many Images, every Image intrinsically belongs to a Tutorial. So Images should be embedded into the Tutorial document.
* If we frequently need to query both of collections on their own, we should normalize the data into two separate collections, even if they are closely related. Imagine that in our Tutorial Blog, we have a widget called "Recent Images", and Images could belong to separated Tutorials. This means that we’re gonna query Images on their own collections without necessarily querying for the Tutorials themselves.

So, apply this third criterion, we come to the conclusion that we should actually normalize the data. Another way is still embed Images \(with appropriate fields\) in Tutorial document, but also create Images collection.

All of this shows that we should really look all the three criteria together rather than just one of them in isolation. They are not really completely right or completely wrong ways of modeling our data.

## Two Ways:

1. **Reference Data Models \(Normalization\)**
   * we keep all the documents ‘separated’ which is exactly what ‘normalized’
2. **Embedded Data Models \(Denormalization\)**
   * embedding the related documents right into the main document

## **1. Reference Data Models \(Normalization\)**

{% tabs %}
{% tab title="Child Referencing \(Bad Design\)" %}
```javascript
// A Tutorial has many Comments

// Tutorial
{
  _id: "5db579f5faf1f8434098f7f5"
  title: "Tutorial #1",
  author: "bezkoder"
  comments: [ "5db57a03faf1f8434098f7f8", "5db57a04faf1f8434098f7f9" ],
}

// Comments
{
  _id: "5db57a03faf1f8434098f7f8",
  username: "jack",
  text: "This is a great tutorial.",
  createdAt: 2019-10-27T11:05:39.898Z
}

{
  _id: "5db57a04faf1f8434098f7f9",
  username: "mary",
  text: "Thank you, it helps me alot.",
  createdAt: 2019-10-27T11:05:40.710Z
}

/*
- Each tutorial has commentIds array
- When we request Tutorial data, we can easily identify its Comments
- This type of referencing is called "Child Referencing": the parent references its children.
*/

/*
::PROBLEM::
- this array of IDs can become very large if there are lots of children. 
- This is an anti-pattern in MongoDB that we should avoid at all costs.
*/

/*
::SOLN:: 
- That’s why we have Parent Referencing. 
- In each child document we keep a reference to the parent element.
- For example, a Category could have a lot of Tutorials, 
- we don’t want to make a categories array with 200-500 items, 
- so we normalize data with Parent Referencing.
*/ 
```
{% endtab %}

{% tab title="Parent Referencing \(Good Design\)" %}
```javascript
// A Category has a lot of Tutorials

// Category
{
  _id: "5db66dd1f4892d34f4f4451a",  
  name: "Node.js",
  description: "Node.js tutorial",
}

// Tutorials
{ _id: "5db66dcdf4892d34f4f44515",
  title: "Tutorial #1",  
  author: "bezkoder",
  category_id: "5db66dd1f4892d34f4f4451a"
}

{ 
  _id: "5db66dd3f4892d34f4f4451b",
  title: "Tutorial #2",
  author: "bezkoder",
  category_id: "5db66dd1f4892d34f4f4451a"
}

...
```
{% endtab %}
{% endtabs %}

## Case 1: One-to-Many \(Few\) Relationship

{% tabs %}
{% tab title="Schema" %}
```javascript
const Tutorial = mongoose.model(
  "Tutorial",
  new mongoose.Schema({
    title: String,
    author: String,
    images: []
  })
);
```
{% endtab %}

{% tab title="E.g. Insert" %}
```javascript
const createTutorial = function(tutorial) {
  return Tutorial.create(tutorial).then(docTutorial => {
    console.log("\n>> Created Tutorial:\n", docTutorial);
    return docTutorial;
  });
};

const createImage = function(tutorialId, image) {
  console.log("\n>> Add Image:\n", image);
  return Tutorial.findByIdAndUpdate(
    tutorialId,
    {
      $push: {
        images: {
          url: image.url,
          caption: image.caption
        }
      }
    },
    { new: true, useFindAndModify: false }
  );
};

const run = async function() {
  var tutorial = await createTutorial({
    title: "Tutorial #1",
    author: "bezkoder"
  });

  tutorial = await createImage(tutorial._id, {
    path: "sites/uploads/images/mongodb.png",
    url: "/images/mongodb.png",
    caption: "MongoDB Database",
    createdAt: Date.now()
  });
  console.log("\n>> Tutorial:\n", tutorial);

  tutorial = await createImage(tutorial._id, {
    path: "sites/uploads/images/one-to-many.png",
    url: "/images/one-to-many.png",
    caption: "One to Many Relationship",
    createdAt: Date.now()
  });
  console.log("\n>> Tutorial:\n", tutorial);
};

run();
```
{% endtab %}

{% tab title="O/p" %}
```javascript
// Created Tutorial:
{
  images: [],
  _id: 5 db6ab3fd9fbef1c6861b978,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}

// Add Image:
{
  path: 'sites/uploads/images/mongodb.png',
  url: '/images/mongodb.png',
  caption: 'MongoDB Database',
  createdAt: 1572252481890
}

// Tutorial:
{
  images: [{
    url: '/images/mongodb.png',
    caption: 'MongoDB Database'
  }],
  _id: 5 db6ab3fd9fbef1c6861b978,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}

// Add Image:
{
  path: 'sites/uploads/images/one-to-many.png',
  url: '/images/one-to-many.png',
  caption: 'One to Many Relationship',
  createdAt: 1572252483834
}

// Tutorial:
{
  images: [
    {
      url: '/images/mongodb.png',
      caption: 'MongoDB Database'
    },
    {
      url: '/images/one-to-many.png',
      caption: 'One to Many Relationship'
    }
  ],
  _id: 5 db6ab3fd9fbef1c6861b978,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}
```
{% endtab %}

{% tab title="DB Query" %}
```javascript
....
```
{% endtab %}
{% endtabs %}

Now, if we want to embed Images \(with appropriate fields\) in Tutorial document, but also want to query Images on their own collections without necessarily querying for the Tutorials themselves, we can define `Image` model like this:



{% tabs %}
{% tab title="Schema" %}
```javascript
const Image = mongoose.model(
  "Image",
  new mongoose.Schema({
    path: String,
    url: String,
    caption: String,
    createdAt: Date
  })
);
```
{% endtab %}

{% tab title="E.g. Insert" %}
```javascript
const createImage = function(tutorialId, image) {
  return db.Image.create(image).then(docImage => {
    console.log("\n>> Created Image:\n", docImage);
    return db.Tutorial.findByIdAndUpdate(
      tutorialId,
      {
        $push: {
          images: {
            _id: docImage._id,
            url: docImage.url,
            caption: docImage.caption
          }
        }
      },
      { new: true, useFindAndModify: false }
    );
  });
};
```
{% endtab %}

{% tab title="O/p" %}
```javascript
 // Created Tutorial:
 {
   images: [],
   _id: 5 db6af65c90cdd3a2c3038aa,
   title: 'Tutorial #1',
   author: 'bezkoder',
   __v: 0
 }

 // Created Image:
 {
   _id: 5 db6af68c90cdd3a2c3038ab,
   path: 'sites/uploads/images/mongodb.png',
   url: '/images/mongodb.png',
   caption: 'MongoDB Database',
   createdAt: 2019 - 10 - 28 T09: 05: 44.894 Z,
   __v: 0
 }

// Tutorial: 
 {
   images: [{
     _id: 5 db6af68c90cdd3a2c3038ab,
     url: '/images/mongodb.png',
     caption: 'MongoDB Database'
   }],
   _id: 5 db6af65c90cdd3a2c3038aa,
   title: 'Tutorial #1',
   author: 'bezkoder',
   __v: 0
 }

 // Created Image:
 {
   _id: 5 db6af6ac90cdd3a2c3038ac,
   path: 'sites/uploads/images/one-to-many.png',
   url: '/images/one-to-many.png',
   caption: 'One to Many Relationship',
   createdAt: 2019 - 10 - 28 T09: 05: 46.427 Z,
   __v: 0
 }

 // Tutorial:
 {
   images: [
     {
       _id: 5 db6af68c90cdd3a2c3038ab,
       url: '/images/mongodb.png',
       caption: 'MongoDB Database'
     },
     {
       _id: 5 db6af6ac90cdd3a2c3038ac,
       url: '/images/one-to-many.png',
       caption: 'One to Many Relationship'
     }
   ],
   _id: 5 db6af65c90cdd3a2c3038aa,
   title: 'Tutorial #1',
   author: 'bezkoder',
   __v: 0
 }
```
{% endtab %}

{% tab title="DB Query" %}
```javascript
....
```
{% endtab %}
{% endtabs %}



## Case 2: One-to-Many \(Many\) Relationship

Let’s define Tutorial to make One-to-Many Relationship with Comments using References Data Model

{% tabs %}
{% tab title="Schema" %}
```javascript
const Comment = mongoose.model(
  "Comment",
  new mongoose.Schema({
    username: String,
    text: String,
    createdAt: Date
  })
);

const Tutorial = mongoose.model(
  "Tutorial",
  new mongoose.Schema({
    title: String,
    author: String,
    images: [],
    comments: [
      {
        type: mongoose.Schema.Types.ObjectId,
        ref: "Comment"
      }
    ]
  })
);

```
{% endtab %}

{% tab title="E.g. Insert" %}
```javascript
const createComment = function(tutorialId, comment) {
  return db.Comment.create(comment).then(docComment => {
    console.log("\n>> Created Comment:\n", docComment);

    return db.Tutorial.findByIdAndUpdate(
      tutorialId,
      { $push: { comments: docComment._id } },
      { new: true, useFindAndModify: false }
    );
  });
};

const run = async function() {
  var tutorial = await createTutorial({
    title: "Tutorial #1",
    author: "bezkoder"
  });

  tutorial = await createComment(tutorial._id, {
    username: "jack",
    text: "This is a great tutorial.",
    createdAt: Date.now()
  });
  console.log("\n>> Tutorial:\n", tutorial);

  tutorial = await createComment(tutorial._id, {
    username: "mary",
    text: "Thank you, it helps me alot.",
    createdAt: Date.now()
  });
  console.log("\n>> Tutorial:\n", tutorial);
};
```
{% endtab %}

{% tab title="O/p" %}
```javascript
// >> Created Tutorial:
{
  images: [],
  comments: [],
  _id: 5db6baf8186b350fc0f2a88a,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}

// >> Created Comment:
{
  _id: 5 db6bafa186b350fc0f2a88b,
  username: 'jack',
  text: 'This is a great tutorial.',
  createdAt: 2019 - 10 - 28 T09: 55: 06.127 Z,
  __v: 0
}

// >> Tutorial:
{
  images: [],
  comments: [5db6bafa186b350fc0f2a88b],
  _id: 5 db6baf8186b350fc0f2a88a,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}

// >> Created Comment:
{
  _id: 5db6bafb186b350fc0f2a88c,
  username: 'mary',
  text: 'Thank you, it helps me alot.',
  createdAt: 2019 - 10 - 28 T09: 55: 07.150 Z,
  __v: 0
}

// >> Tutorial:
{
  images: [],
  comments: [5db6bafa186b350fc0f2a88b, 5db6bafb186b350fc0f2a88c],
  _id: 5 db6baf8186b350fc0f2a88a,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}
```
{% endtab %}

{% tab title="DB Query" %}
```javascript
const getTutorialWithPopulate = function(id) {
  return db.Tutorial.findById(id).populate("comments");
};


/*
// populated Tutorial:
{
  images: [],
  comments: [
    {
      _id: 5db6bc1630d4f50840fd552b,
      username: 'jack',
      text: 'This is a great tutorial.',
      createdAt: 2019 - 10 - 28 T09: 59: 50.642 Z,
      __v: 0
    },
    {
      _id: 5db6bc1630d4f50840fd552c,
      username: 'mary',
      text: 'Thank you, it helps me alot.',
      createdAt: 2019 - 10 - 28 T09: 59: 50.676 Z,
      __v: 0
    }
  ],
  _id: 5db6bc1430d4f50840fd552a,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}
  */
```
{% endtab %}
{% endtabs %}

...

## Case 3: One-to-Many \(aLot\) Relationship

{% tabs %}
{% tab title="Schema" %}
```javascript
const Category = mongoose.model(
  "Category",
  new mongoose.Schema({
    name: String,
    description: String
  })
);

const Tutorial = mongoose.model(
  "Tutorial",
  new mongoose.Schema({
    title: String,
    author: String,
    images: [],
    comments: [
      {
        type: mongoose.Schema.Types.ObjectId,
        ref: "Comment"
      }
    ],
    category: {
      type: mongoose.Schema.Types.ObjectId,
      ref: "Category"
    }
  })
);
```
{% endtab %}

{% tab title="E.g. Insert" %}
```javascript
const createCategory = function(category) {
  return db.Category.create(category).then(docCategory => {
    console.log("\n>> Created Category:\n", docCategory);
    return docCategory;
  });
};

const addTutorialToCategory = function(tutorialId, categoryId) {
  return db.Tutorial.findByIdAndUpdate(
    tutorialId,
    { category: categoryId },
    { new: true, useFindAndModify: false }
  );
};

const run = async function() {
  var tutorial = await createTutorial({
    title: "Tutorial #1",
    author: "bezkoder"
  });

 var category = await createCategory({
    name: "Node.js",
    description: "Node.js tutorial"
  });

  tutorial = await addTutorialToCategory(tutorial._id, category._id);
  console.log("\n>> Tutorial:\n", tutorial);
};
```
{% endtab %}

{% tab title="O/p" %}
```javascript
// >> Created Tutorial:
{
  images: [],
  comments: [],
  _id: 5 db6c27ed15b6649e8efe3e3,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}

// >> Created Category:
{
  _id: 5 db6c280d15b6649e8efe3e4,
  name: 'Node.js',
  description: 'Node.js tutorial',
  __v: 0
}

// >> Tutorial:
{
  images: [],
  comments: [],
  _id: 5 db6c27ed15b6649e8efe3e3,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0,
  category: 5 db6c280d15b6649e8efe3e4
}
```
{% endtab %}

{% tab title="DB Query" %}
```javascript
const getTutorialsInCategory = function(categoryId) {
  return db.Tutorial.find({ category: categoryId })
    .populate("category", "name -_id")
    .select("-comments -images -__v");
};

const run = async function() {
  var tutorial = await createTutorial({
    title: "Tutorial #1",
    author: "bezkoder"
  });

  var category = await createCategory({
    name: "Node.js",
    description: "Node.js tutorial"
  });

  await addTutorialToCategory(tutorial._id, category._id);

  var newTutorial = await createTutorial({
    title: "Tutorial #2",
    author: "bezkoder"
  });

  await addTutorialToCategory(newTutorial._id, category._id);

  var tutorials = await getTutorialsInCategory(category._id);
  console.log("\n>> all Tutorials in Cagetory:\n", tutorials);
};


/*

// >> Created Tutorial:
{
  images: [],
  comments: [],
  _id: 5 db6c3e5d601484404b92b17,
  title: 'Tutorial #1',
  author: 'bezkoder',
  __v: 0
}

// >> Created Category:
{
  _id: 5 db6c3e7d601484404b92b18,
  name: 'Node.js',
  description: 'Node.js tutorial',
  __v: 0
}

// >> Created Tutorial:
{
  images: [],
  comments: [],
  _id: 5 db6c3e7d601484404b92b19,
  title: 'Tutorial #2',
  author: 'bezkoder',
  __v: 0
}

// >> all Tutorials in Cagetory:
[{
    _id: 5 db6c3e5d601484404b92b17,
    title: 'Tutorial #1',
    author: 'bezkoder',
    category: {
      name: 'Node.js'
    }
  },
  {
    _id: 5 db6c3e7d601484404b92b19,
    title: 'Tutorial #2',
    author: 'bezkoder',
    category: {
      name: 'Node.js'
    }
  }
]

*/

```
{% endtab %}
{% endtabs %}





### Summary

* We don’t have any standard or specific rule for all cases, it depends on the ways your application queries and updates data. You should identify the problems in your application’s use cases first, then model your data to answer the questions in the most efficient way.
* With one-to-few and one-to-many relationships, in general, think about Embedding first.
* **One-to-aLot** relationship is usually treated by Reference instead of Embedding.
* **Use Embedding** when data is mostly read but rarely updated, and when two models belong intrinsically together.
* **Use Referencing** when data is updated a lot, and you need to frequently query a collection on its own.
* **Never allow arrays to grow indefinitely**. 
  * Therefore, use _Child Referencing_ for one-to-many relationships,
  * and _Parent Referencing_ for One-to-aLot relationships.

