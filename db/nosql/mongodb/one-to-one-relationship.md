# One to One Relationship

## Two Ways:

1. **Reference Data Models \(Normalization\)**
   * Obj A has Obj B \(ID\)
   * Obj A connects to the Obj B by reference to Obj B i
2. **Embedded Data Models \(Denormalization\)**
   * Instead of using a reference, 
   * Obj A contains the whole Obj B, 
   * or Obj B is embedded inside Obj A

### E.g. \(Identifier & Customer\)

* One Customer has only one Identifier.
* One Identifier belongs to only one Customer.



## **1. Reference Data Models \(Normalization\)**

{% tabs %}
{% tab title="Schema" %}
```javascript
const Customer = mongoose.model(
  "Customer",
  new mongoose.Schema({
    name: String,
    age: Number,
    gender: String
  })
);


const Identifier = mongoose.model(
  "Identifier",
  new mongoose.Schema({
    cardCode: String,
    customer: {
      type: mongoose.Schema.Types.ObjectId,
      ref: "Customer"
    }
  })
);
```
{% endtab %}

{% tab title="E.g. Insert" %}
```javascript
const Customer = require("./models/Customer");
const Identifier = require("./models/Identifier");

const createCustomer = function(name, age, gender) {
  const customer = new Customer({ name, age, gender });

  return customer.save();
};

const createIdentifier = function(cardCode, customer) {
  const identifier = new Identifier({ cardCode, customer});

  return identifier.save();
};

createCustomer("bezkoder", 29, "male")
  .then(customer => {
    console.log("> Created new Customer\n", customer);
    
    const customerId = customer._id.toString();
    return createIdentifier(customerId.substring(0, 10).toUpperCase(), customerId);
  })
  .then(identifier => {
    console.log("> Created new Identifier\n", identifier);
  })
  .catch(err => console.log(err));
```
{% endtab %}

{% tab title="E.g. Data" %}
```javascript
// Created new Customer
{
    _id: 5da135bd61a1dd3e9c2a6e81,
    name: 'bezkoder',
    age: 29,
    gender: 'male',
    __v: 0
}

// Created new Identifier
{
    _id: 5da135bf61a1dd3e9c2a6e82,
    cardCode: '5DA135BD61',
    customer: 5da135bd61a1dd3e9c2a6e81,
    __v: 0
}
```
{% endtab %}

{% tab title="DB Query" %}
```javascript
const getAllIdentifiers = async function() {
  const identifiers = await Identifier.find();
  console.log("> All Identifiers\n", identifiers);
};


/*
[
  {
    _id: 5da135bf61a1dd3e9c2a6e82,
    cardCode: '5DA135BD61',
    customer: 5da135bd61a1dd3e9c2a6e81,
    __v: 0
  },
  ....
]
*/

const getAllIdentifiersWithCustomer = async function() {
  const identifiers = await Identifier.find().populate("customer");
  console.log("> All Identifiers\n", identifiers);
};

/*
[
  {
    _id: 5 da135bf61a1dd3e9c2a6e82,
    cardCode: '5DA135BD61',
    customer: {
      _id: 5 da135bd61a1dd3e9c2a6e81,
      name: 'bezkoder',
      age: 29,
      gender: 'male',
      __v: 0
    },
    __v: 0
  },
  ....
]
*/
```
{% endtab %}
{% endtabs %}



## 2. Embedded Data Models \(Denormalization\)

{% tabs %}
{% tab title="Schema" %}
```javascript
const CustomerSchema = new mongoose.Schema({
  name: String,
  age: Number,
  gender: String
});

const Customer = mongoose.model("Customer", CustomerSchema);

const Identifier = mongoose.model(
  "Identifier",
  new mongoose.Schema({
    cardCode: String,
    customer: CustomerSchema
  })
);
```
{% endtab %}

{% tab title="E.g. Insert" %}
```javascript

const createCustomer = function(name, age, gender) {
  const customer = new Customer({
    name,
    age,
    gender
  });

  return customer.save();
};

const createIdentifier = function(cardCode, customer) {
  const identifier = new Identifier({
    cardCode,
    customer
  });

  return identifier.save();
};

createCustomer("bezkoder", 29, "male")
  .then(customer => {
    console.log("> Created new Customer\n", customer);

    return createIdentifier(
      customer._id.toString().substring(0, 10).toUpperCase(),
      customer
    );
  })
  .then(identifier => {
    console.log("> Created new Identifier\n", identifier);
  })
  .catch(err => console.log(err));
```
{% endtab %}

{% tab title="E.g. Data" %}
```javascript
// Created new Customer
{
  _id: 5da1406de666c118c89bba28,
  name: 'bezkoder',
  age: 29,
  gender: 'male',
  __v: 0
}

// Created new Identifier
{
  _id: 5da1406fe666c118c89bba29,
  cardCode: '5DA1406DE6',
  customer: {
    _id: 5da1406de666c118c89bba28,
    name: 'bezkoder',
    age: 29,
    gender: 'male',
    __v: 0
  },
  __v: 0
}
```
{% endtab %}

{% tab title="DB Query" %}
```javascript
const showAllIdentifier = async function() {
  const identifiers = await Identifier.find();
  console.log("> All Identifiers\n", identifiers);
};


// All Identifiers
[{
  _id: 5 da1406fe666c118c89bba29,
  cardCode: '5DA1406DE6',
  customer: {
    _id: 5 da1406de666c118c89bba28,
    name: 'bezkoder',
    age: 29,
    gender: 'male',
    __v: 0
  },
  __v: 0
}]
```
{% endtab %}
{% endtabs %}



## Referencing or Embedding for One-to-One Relationships

* To make One-to-One Relationship between documents, we can reference or embed a document in the other. 

**Which one is better?**

* Now remind what we’ve done and you can see that we have to use an additional function called `populate()` after `find()` function for Referenced Data Model.
* Embedding stores related information directly inside the objects. So we only use `find()` function to get everything. It gives us better performance with a single query. This Model also helps us update the embedded data in just one query using [Dot Notation](https://docs.mongodb.com/manual/core/document/#document-dot-notation).

So the answer is that modeling **One-to-One relationships** with "**Embedded documents" is the better choice.**

