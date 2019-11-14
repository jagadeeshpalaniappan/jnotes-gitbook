---
description: Is JavaScript Object-Oriented Programming or Functional Programming?
---

# Is JavaScript OOP or FP?

```javascript
JavaScript is 'scripting language' or procedural Language
 - that supports 'Object Oriented Programming (OOP)' and 'FunctionalProgramming (FP)'

JavaScript uses 'prototype -based inheritance' instead of class based.
- In JavaScript, even 'function' is also an object (that means it has properties and methods)



## Object-Oriented Programming
 - EAIP
 - Encapsulation
 - Abstraction
 - Inheritance
 - Polymorphism (method overloading/overiding) // (Note: JavaScript do not suport this)


## FP:
- focus on computations, 'care only about return values'
- complete separation between the '(data) of a program' and the 'behaviors of a program (methods)'
- 'all objects created in FP are immutable' 
- Shared state is avoided 
- has only 'pure functions', 

pure functions: 
- 'fn return value only depends on the input'
- 'no shared states', 
- separates 'data & methods' and gives 'high abstractions'

```

## Object-Oriented Programming

OOP “is a programming paradigm based on the concept of “objects”, 

* which may contain **data**, in the form of _fields_ \(often known as _`attributes`\)_
* and **code**, in the form of procedures \(often known as _`methods`\)_ 

A feature of objects is that 

* an object’s `procedures` can access and often **modify** the `data fields` of the object 
* with which they are associated \(objects have a notion of “this” or “self”\)”, 
* which essentially means, altering the ‘state’ of the object.

Most OOP languages, 

* Class Based \(objects are instances of a class\)
  * individual entities which interact with each other\)
* But JavaScript is Prototype based.



## Functional Programming

FP is a language that focuses on the **computation** of `pure functions` 

What exactly do we mean by `pure`?

* There is a complete separation between the data of a program, and the behaviors of a program
* All objects created in functional programming are **immutable** \(once something is created, it can’t be changed\)
* Shared state is avoided \(objects do not share scope with other objects\)
* Adherence to pure functions \(explained below\)

## Pure functions <a id="22a2"></a>

A pure function is a function where:

* The `return value only depends on the input` 
  * \(if you input the same value, you will _always_ return the same value\)
* There are `no side effects` 
  * \(for example: no network or database calls which could affect the return value\)
* They `do not modify the passed data` 
  * We _only_ want to describe how the input will be changed \(think destructive vs non-destructive\)

Here are some examples of an impure function:

```javascript
/* ################# Not a PURE Functions ################# */

function number(num){
  num * Math.random()
}
// this fn return value may vary even if the input is same 


function hello(greeting){
  console.log(greeting)
}
// this fn has 'side-effect’, console logging may or maynot work

var totalPeople = 10
function totalVotes(votes){
 return votes * totalPeople
}
//  this fn, depends on a variable outside of its scope (shared state!)
```

Here’s an example of a pure function:

```javascript
/* ################# Not a PURE Function ################# */

function plusTwo(num){
  return num + 2
}
// this fn return value only depends on the input.
```

## So, which is better? <a id="d1d1"></a>

OOP team argues that the 

* `concept of inheritance` \(new objects taking on the attributes/methods of existing objects letting us reuse more code\)
* `encapsulation` \(the data and methods related to a certain object being bound together, creating independent, protected entities\) makes it easier to manage and manipulate data. 

FP team argues that the 

* `'separation of data and methods'` and `'high level of abstraction'`
* leave less room for errors.

It seems the general consensus is that OOP and FP are better depending on the situation,.

