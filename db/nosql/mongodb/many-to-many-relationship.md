# Many to Many Relationship

**E.g. \(Tutorial Blog App\)**

* A Tutorial can have many Tags 
* A Tag can point to many Tutorials

**References or Embedding for Many-to-Many Relationships** 

For Embedded Data Models, you can see that we can get all the data about Tutorial with its Tags \(or Tag with its Tutorials\) at the same time, our application will need few queries to the database. It will increase our performance.

But when the data become larger and larger, duplicates is inevitable. And the risk is so serious in case we want to update document, even just a field, we have to find and update two place.

For example, if you want to change the name of tagA, you must have to change not only that Tag’s document but also find the Tutorial that contains the Tag, find that Tag exactly, then update the field. So terrible!

Hence, with Many-to-Many relationship, 

* we **always** use **Data References** or Normalizing the data.





## **Reference Data Models \(Normalization\)**

{% tabs %}
{% tab title="Schema" %}
```javascript
const Tag = mongoose.model(
  "Tag",
  new mongoose.Schema({
    name: String,
    slug: String,
    tutorials: [
      {
        type: mongoose.Schema.Types.ObjectId,
        ref: "Tutorial"
      }
    ]
  })
);

const Tutorial = mongoose.model(
  "Tutorial",
  new mongoose.Schema({
    title: String,
    author: String,
    tags: [
      {
        type: mongoose.Schema.Types.ObjectId,
        ref: "Tag"
      }
    ]
  })
);
```
{% endtab %}

{% tab title="E.g. Insert" %}
```javascript

const createTutorial = function(tutorial) {
  return db.Tutorial.create(tutorial).then(docTutorial => {
    console.log("\n>> Created Tutorial:\n", docTutorial);
    return docTutorial;
  });
};

const createTag = function(tag) {
  return db.Tag.create(tag).then(docTag => {
    console.log("\n>> Created Tag:\n", docTag);
    return docTag;
  });
};

const addTagToTutorial = function(tutorialId, tag) {
  return db.Tutorial.findByIdAndUpdate(
    tutorialId,
    { $push: { tags: tag._id } },
    { new: true, useFindAndModify: false }
  );
};

const addTutorialToTag = function(tagId, tutorial) {
  return db.Tag.findByIdAndUpdate(
    tagId,
    { $push: { tutorials: tutorial._id } },
    { new: true, useFindAndModify: false }
  );
};

const run = async function() {
  var tut1 = await createTutorial({
    title: "Tut #1",
    author: "bezkoder"
  });

  var tagA = await createTag({
    name: "tagA",
    slug: "tag-a"
  });

  var tagB = await createTag({
    name: "tagB",
    slug: "tag-b"
  });

  var tutorial = await addTagToTutorial(tut1._id, tagA);
  console.log("\n>> tut1:\n", tutorial);

  var tag = await addTutorialToTag(tagA._id, tut1);
  console.log("\n>> tagA:\n", tag);

  tutorial = await addTagToTutorial(tut1._id, tagB);
  console.log("\n>> tut1:\n", tutorial);

  tag = await addTutorialToTag(tagB._id, tut1);
  console.log("\n>> tagB:\n", tag);

  var tut2 = await createTutorial({
    title: "Tut #2",
    author: "zkoder"
  });

  tutorial = await addTagToTutorial(tut2._id, tagB);
  console.log("\n>> tut2:\n", tutorial);

  tag = await addTutorialToTag(tagB._id, tut2);
  console.log("\n>> tagB:\n", tag);
};

mongoose
  .connect("mongodb://localhost/bezkoder_db", {
    useNewUrlParser: true,
    useUnifiedTopology: true
  })
  .then(() => console.log("Successfully connect to MongoDB."))
  .catch(err => console.error("Connection error", err));

run();
```
{% endtab %}

{% tab title="O/p" %}
```javascript
Successfully connect to MongoDB.

>> Created Tutorial:
 { tags: [],
  _id: 5e417363316cab53182888d8,
  title: 'Tut #1',
  author: 'bezkoder',
  __v: 0 }

>> Created Tag:
 { tutorials: [],
  _id: 5e417363316cab53182888d9,
  name: 'tagA',
  slug: 'tag-a',
  __v: 0 }

>> Created Tag:
 { tutorials: [],
  _id: 5e417363316cab53182888da,
  name: 'tagB',
  slug: 'tag-b',
  __v: 0 }

>> tut1:
 { tags: [ 5e417363316cab53182888d9 ],
  _id: 5e417363316cab53182888d8,      
  title: 'Tut #1',
  author: 'bezkoder',
  __v: 0 }

>> tagA:
 { tutorials: [ 5e417363316cab53182888d8 ],
  _id: 5e417363316cab53182888d9,
  name: 'tagA',
  slug: 'tag-a',
  __v: 0 }

>> tut1:
 { tags: [ 5e417363316cab53182888d9, 5e417363316cab53182888da ],
  _id: 5e417363316cab53182888d8,
  title: 'Tut #1',
  author: 'bezkoder',
  __v: 0 }

>> tagB:
 { tutorials: [ 5e417363316cab53182888d8 ],
  _id: 5e417363316cab53182888da,
  name: 'tagB',
  slug: 'tag-b',
  __v: 0 }

>> Created Tutorial:
 { tags: [],
  _id: 5e417363316cab53182888db,
  title: 'Tut #2',
  author: 'zkoder',
  __v: 0 }

>> tut2:
 { tags: [ 5e417363316cab53182888da ],
  _id: 5e417363316cab53182888db,
  title: 'Tut #2',
  author: 'zkoder',
  __v: 0 }

>> tagB:
 { tutorials: [ 5e417363316cab53182888d8, 5e417363316cab53182888db ],
  _id: 5e417363316cab53182888da,
  name: 'tagB',
  slug: 'tag-b',
  __v: 0 }
```
{% endtab %}

{% tab title="DB Query" %}
```javascript
const getTutorialWithPopulate = function(id) {
  return db.Tutorial.findById(id).populate("tags");
};

const getTagWithPopulate = function(id) {
  return db.Tag.findById(id).populate("tutorials");
};

const run = async function() {
  // ...

  // add this
  tutorial = await getTutorialWithPopulate(tut1._id);
  console.log("\n>> populated tut1:\n", tutorial);

  tag = await getTagWithPopulate(tag._id);
  console.log("\n>> populated tagB:\n", tag);
};
```
{% endtab %}

{% tab title="O/p" %}
```javascript
>> populated tut1:
 { tags:
   [ { tutorials: [Array],
       _id: 5e417363316cab53182888d9,
       name: 'tagA',
       slug: 'tag-a',
       __v: 0 },
     { tutorials: [Array],
       _id: 5e417363316cab53182888da,
       name: 'tagB',
       slug: 'tag-b',
       __v: 0 } ],
  _id: 5e417363316cab53182888d8,
  title: 'Tut #1',
  author: 'bezkoder',
  __v: 0 }

>> populated tagB:
 { tutorials:
   [ { tags: [Array],
       _id: 5e417363316cab53182888d8,
       title: 'Tut #1',
       author: 'bezkoder',
       __v: 0 },
     { tags: [Array],
       _id: 5e417363316cab53182888db,
       title: 'Tut #2',
       author: 'zkoder',
       __v: 0 } ],
  _id: 5e417363316cab53182888da,
  name: 'tagB',
  slug: 'tag-b',
  __v: 0 }
```
{% endtab %}
{% endtabs %}





