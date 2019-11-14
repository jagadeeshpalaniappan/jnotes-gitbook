# 1. TypeScript First

## TypeScript Compiler

```text
npm install -g typescript

tsc –v

tsc hello.ts
```

```text
node hello.js
```

Watch changes in the ts file:

```text
tsc -w hello.ts
```

Inline Configuration \(-t target\)

```text
tsc -t ES6 -w hello.ts
```

However if we are want to watch a whole directory we need to use a configuration file.

Create a TS configuration file \(tsconfig.json\)

```text
tsc —init
```

It watches the entire directory and coverts TS into JS

```text
tsc -w
```

## let

### Global Block Scope

#### In Other Languages

```typescript
{
    // This is a block
}

// This is not part a block
```

#### In JavaScript

```typescript
{
  var a = "block";
}
console.log(a);   // block  (it works in JavaScript)
```

### Function Block Scope

```typescript
function hello() {
    var a = "function";
}
hello();
console.log(a);   //ERROR: Uncaught ReferenceError: a is not defined(…)
                  // 'a' variable is only accesisble in that function scope
```

```typescript
function hello() {

    var a = "function";
    for (var i = 0; i < 10; i++) {
        // same variable 'a'
        var a = "block";
    }

    console.log(a);  // 'block' will be printed
    // In other kanguages, 'function' will be printed

    // becuase for(..) {... block level scope....}
}
hello();
```

Common Work Around / Solution for this is,

## IIFE \(Immediately Invoked Fn Expression\)

```typescript
function hello() {
    var a = "function";

    for (var i=0; i<5; i++) {
        (function() {
            var a = "block";
        })();
    }
    console.log(a);
}
hello();
```

In this,

```typescript
(function() {
    var a = "block";
})();
```

is equal to,

```typescript
function something() {
  var a = "block";
}
something();
```

* It’s a function that we call immediately after defining it.
* Since functions have their own scope, using an IIFE has the same effect
* the variable a inside the IIFE isn’t visible outside the IIFE.

Most Common Mistake

```typescript
var funcs = [];
for (var i = 0; i < 5; i ++) {
    // 'y' is accessible even outside the for loop
    var y = i;  
    funcs.push(function () {
        console.log(y);
    })
}

// 'y' can be accessible here
funcs.forEach(function (func) {

    // 'y' can be accessible here
    func()
});
```

What gets printed out?

You might expect

```typescript
0
1
2
3
4
```

But the answer is,

```typescript
4
4
4
4
4
```

* The reason for this is that the variable y is not block level, 
* it doesn’t only exist inside its enclosing {} 
* In fact it’s a global variable and by the time any of the functions are called it’s already been set to 4.
* It is equal to

  ```typescript
  var funcs = [];
  var y;
  for (var i = 0; i < 5; i ++) {
      y = i;
      funcs.push(function () {
          console.log(y);
      })
  }
  funcs.forEach(function (func) {
      func()
  });
  ```

In the above example, if we replace var y = i with let y = i then the variable y only exists inside it’s block

```typescript
var funcs = [];
for (var i = 0; i < 5; i ++) {
    let y = i;  // 'y' is accessible only inside the for loop
    funcs.push(function () {
        console.log(y);
    })
}

// 'y' cannot be accessible here
funcs.forEach(function (func) {
    // 'y' cannot be accessible here
    func()
});
```

And so executing this now results in:

```typescript
0
1
2
3
4
```

The above construct is so common we have a shortcut, we can declare the index variable i with let in the for loop expression

```typescript
var funcs = [];
for (let i = 0; i < 5; i += 1) {
    funcs.push(function () {
        console.log(i);
    })
}
funcs.forEach(function (func) {
    func()
});
```

```typescript
0
1
2
3
4
```

Even though let i = 0 is strictly declared outside of the for block { }, any variables declared in the for loop expression with let has block level scope in the for loop.

**Summary**

`let` is a very important addition the javascript language in ES6.

* It’s not a replacement to var
* var can still be used even in ES6 and has the same semantics as ES5.
* It is recommended to use `let` instead of `var` \(unless, any specific reason\)

## const

`let` and `var` 1. Value can be initalized anytime 2. It is **Mutable** 3. It is **Block Scoping**

```text
1. It must be immediately initialised with a value
2. It is **Immutable** (can’t be changed afterwards)
3. It is **Block Scoping**


```typescript

// 1. It must be immediately initialised with a value
// Declaring a const variable (without initializing the value is NOT possible)
const foo; // SyntaxError: Missing initializer in const declaration

// const variable should be always (initialized and cannot be modified further)
const foo = 100;

// 2. It is **Immutable** (can’t be changed afterwards)
const foo = 100;
foo = 101; // TypeError: `foo` is read-only

// -or-
// In object variable 'foo' only has the reference of that obj 
const foo = {}; 
// Trying to set new reference location is NOT possible
foo = {}; // TypeError: Assignment to constant variable.

// So the value of the object can be changed,
const foo = {}; 
foo.prop1 = 'Value1';
// It is possible
foo.prop1 = 'Value2';


// But there are other ways in JavaScript to immute (or freeze) the object.

const foo = Object.freeze({});
foo.prop1 = 123;
console.log(foo.prop1) // undefined  (Value is Not Changed) and (No Error), 
// if use "use strict" mode, we get error




// 3. It is **Block Scoping**
function func() {
    if (true) {
        // 'tmp' is accessible only in this if block {...}
        const tmp = 123;
    }

    // 'tmp' is NOT accessible here (accessible only inside that if block{..})
    console.log(tmp); // Uncaught ReferenceError: tmp is not defined
}
func();
```

## Template Strings

```typescript
// All are same
var multiLineString1 = 'hello\n' +
    'world\n' +
    'my\n' +
    'name\n' +
    'is\n' +
    'Jagadeesh\n';


let multiLineString2 = `
hello
world
my
name
is
Jagadeesh`;


// Variable Substitution  ${variableName}

let myName = 'Jagadeesh';

let multiLineString3 = `hello
world
my
name
is
${myName}`;
console.log(multiLineString3);
```

Fat Arrow Functions

## Fat Arrow Functions

Javascript has **First Class Function**

* Means: In JavaScript functions can be themselves be passed around like any other value, even as arguments to other functions.

```typescript
// *** 1. First Class Function ***
// E.g. we can pass a fn as param to the setTimeout function
var myFn = function() {
    console.log("setTimeout called!");
};
setTimeout(myFn, 1000);

// Passed Annonymous Fn
setTimeout(function() {
    console.log("setTimeout called!");
}, 1000);


// *** 2. Fat Arrow Syntax ***
// ES6 introduced new syntax for Annonymous Fn (Fat Arrow Syntax)

setTimeout(() => {
    console.log("setTimeout called!")
}, 1000);

// If the function contains only one expression:
// we can write without block {...}
setTimeout(() => console.log("setTimeout called!"), 1000);

// With Params:
let add = function(a,b) {
    return a + b;
};

// if it has only one expression, that stmnt result automatically returned
// (NO need to use 'return')
let add = (a,b) => a + b;


// *** 2. 'this' Usage ***

let obj1 = {
    name: 'Jagadeesh',
    sayLater: function() {

        // value of 'this' is based on the calling context 
        // in this case it is 'obj1'
        console.log(this.name);
    }
};
obj.sayLater(); // Jagadeesh




let obj1 = {
    name: 'Jagadeesh',
    sayLater: function () {

        // 'this' inside annonymous fn:
        setTimeout(function () {
            // value of 'this' is based on the calling context 
            // in this case it is NOT 'obj1'
            // It is based on the **Calling context**
            console.log(this.name);
        }, 1000);

    }
};
obj.sayLater();  // 'undefined'

/*
Reason: the value of 'this' in a function depends on how the function is called
- For the anonymous function,
        //  -it totally 'depends' where you are running
        //  -it can be 'undefined' or 'global' obj depending on if you are running in strict mode or not. 
        //  -In node it’s an internal timeout object.
- But in any case isn’t going to be obj
- This **instability** of 'this' is an incredibly common problem in javascript -- that has affected JavaScript in early days.
- But still we have some work around (in ES5) to solve this problem,
    -Assign this to another variable
    -usually called 'self' or vm , then use 'self' in fn body
*/

let obj1 = {
    name: 'Jagadeesh',
    sayLater: function () {

        // Assign 'obj1' to 'self'
        let self = this; 
        console.log(self);

        setTimeout(function () {
            // Use 'self' instead of 'this'
            console.log(self.name); // 'Jagadeesh'

        }, 1000);
    }
};

/*
But in ES6 we can do better,
    - if we use 'fat arrow' syntax, 
    - the value of this inside a fat arrow fn will be the same as the value of this outside the fat arrow fn.
*/

let obj = {
    name: 'Jagadeesh',
    sayLater: function () {

        // `this` points to obj
        console.log(this); 

        // Using 'fat arrow' syntax
        setTimeout(() => {
            // `this` points to obj
            console.log(this); 
            console.log(this.name); //'Jagadeesh' 
        }, 1000);
    }
};
obj.sayLater();
```

## Destructuring

Destructuring is a way of extracting values into variables from data stored in objects and arrays.

```typescript
// *** 1. Object Destructuring ***

// Let’s imagine we have an object :
const obj = {first: 'Asim', last: 'Hussain', age: 39 };

// We want to extract the first and last properties into local variables (without ES6)

const f = obj.first;
const l = obj.last;
console.log(f); // Asim
console.log(l); // Hussain

// With ES6,
const {first: f, last: l} = obj;
console.log(f); // Asim
console.log(l); // Hussain

// -or-
const {first: first, last: last} = obj;
console.log(first); // Asim
console.log(last); // Hussain

// -or-
// {prop1} is short for {prop1: prop1}
const {first, last} = obj;
console.log(first); // Asim
console.log(last); // Hussain


// *** 2. Array Destructuring ***

const arr = ['a', 'b', 'c', 'd'];
const [x, y] = arr;
console.log(x); // a
console.log(y); // b


// *** 3. Function Parameter Destructuring ***

// Typically if we want to pass multiple params to a function, 
// with some optional parameters, we would pass it like this

function f(options) {
  console.log(options.x);
}
f({x:1}); // 1

// Now we can define the function parameter list as an object destructure pattern

function f({x}) {
  console.log(x); // Refer to x directly
}
f({x:1}); // 1

// In addition to that, we can also set **default values** for 'parameters'

function f({x=0}) {
  console.log(x);
}
f({}); // 0


// Destructuring is a useful feature of ES6, 
// - with it we can extract values from objects and arrays with ease.
// - easy way to provide optional parameters , with default values
```

## For Of

....

```typescript
// *** 1. For & ForEach (Array Iteration) ***

// In ES5 javascript,
let array = [1,2,3];
for (let i = 0; i < array.length; i++) {
  console.log(array[i]);
}
// 1
// 2
// 3

let array = [1,2,3];
array.forEach(function (value) {
  console.log(value);
});

/*
- It’s slightly shorter -but has a few downsides:
    - You can’t 'break' out of this loop 
    - You can’t 'return' from the enclosing function
*/


// *** 2. for-in (Obj Iteration) ***

var obj = { a:1, b:2 };
for (let prop in obj) {
    console.log(prop);
}
// a
// b

// Also can iterate array, gives you only 'index'
let array = [10,20,30];
for (let index in array) {
  console.log(index);
  // console.log(array[index]);
});
// 0
// 1
// 2


let array = [10,20,30];
for (let index in array) {
  console.log(typeof(index));
};
// string
// string
// string

// The 'index' variable is a 'string' ideally it should be 'number', 
// for-in with arrays converts the index to a string


// *** 2. for-of ***
// - in ES6 we have a new syntax called 'for-of'

let array = [10,20,30];
for (var value of array) {
  console.log(value);
}
// 10
// 20
// 30


// It works with break, continue, and return

/*
- **for–in** loop is for looping over object properties.
- **for–of** loop is for looping over the values in an array.
- **for–of** is not just for arrays. 
    -It also works on most array-like objects
    -including the new Set and Map types
*/
```

## Map & Set

```typescript
// *** 1. Using Object as a Map ***
// In ES5, only data structure we had to map keys to values was an Object { key: 'value' }

let obj = {key: "value", a: 1}
console.log(obj.a); // 1
console.log(obj['key']); // "value"

// However it does have a few drawbacks

// Inherited Objects (Prototype Inheritance)
let base = { a:1, b:2 };
let obj = Object.create(base);
obj[c] = 3;
for (prop in obj) {
    console.log(prop)
}    
// a
// b
// c
// it printed all parent properties too

// what if we need keys that belong to the current object only?

// In ES5, We can use 'hasOwnProperty' to know the key is belongs to current object or not

let base = { a:1, b:2 };
let obj = Object.create(base);
obj[c] = 3;
for (prop in obj) {
    if (obj.hasOwnProperty(prop)) {
        console.log(prop)
    }
}
// c

// But what if we overide this function 'hasOwnProperty'  :) :)

let base = { a:1, b:2 };
let obj = Object.create(base);
obj.c = 3;
obj.hasOwnProperty = 4;
for (prop in obj) {

    // TypeError: Property 'hasOwnProperty' is not a function
    if (obj.hasOwnProperty(prop)) {
        console.log(prop)
    }
}
// c


// Simmilarly, if we overide __proto__ property
let base = {__proto__:1,b:2};
for (prop in obj) console.log(prop)
// b


// *** 2. Map ***
// Map is a new data structure in ES6 
// -it allows you to map 'keys' to 'values' without the drawbacks of using 'Objects'

// We create a map using the new keyword
let map = new Map();


// We can then add entries -- using the set method
let map = new Map();
map.set("A",1);
map.set("B",2);
map.set("C",3);

// -or- (chainable) 
// chainable: means set fn returns the same map instance
let map = new Map()
    .set("A",1)
    .set("B",2)
    .set("C",3);

// -or- (initialise with array of key-value pair array) 
let map = new Map([
    [ "A", 1 ],
    [ "B", 2 ],
    [ "C", 3 ]
]);

// We can get a value --using the get method:
map.get("A");  // 1

// We can check to see if a 'key' is present --using the has method:
map.has("A");  // true

// We can delete entries --using the delete method:
map.delete("A");  // true

// We can check for the size (number of entries) --using the size property:
map.size // 2


// We can empty an entire Map by using the clear method:
map.clear();
map.size;  // 0


// *** Looping over a Map ***
let map = new Map([
    [ "APPLE", 1 ],
    [ "ORANGE", 2 ],
    [ "MANGO", 3 ]
]);

// Using keys():
for (let key of map.keys()) {
    console.log(key);
}
// APPLE
// ORANGE
// MANGO


// Using values():
for (let value of map.values()) {
    console.log(value);
}
// 1
// 2
// 3


// Using entries():
for (let entry of map.entries()) {
    console.log(entry[0], entry[1]);
}
// "APPLE" 1
// "ORANGE" 2
// "MANGO" 3


// Using destructuring we can access the keys and values directly,

for (let [key, value] of map.entries()) {
    console.log(key, value);
}
// "APPLE" 1
// "ORANGE" 2
// "MANGO" 3


// Looping over key-value pairs via entries is so common that this is the default for a Map.

// Therefore we don’t even need to call entries() on a map instance,

for (let [key, value] of map) {
    console.log(key, value);
}
// "APPLE" 1
// "ORANGE" 2
// "MANGO" 3

/*
Important
A distinction between Object and Map is that 
    - Maps record the order in which elements are inserted. 
    - It then replays that order when looping over keys, values or entries.
*/



// *** 3. Set ***
// - Sets are a bit like maps but they only store keys not key-value pairs.
// - They are common in other programming languages but are a new addition to JavaScript in ES6.


// We create a Set using the new keyword, 
let set = new Set();


// We can then add entries by using the add method
let set = new Set();
set.add('APPLE');
set.add('ORANGE');
set.add('MANGO');

// The add method is chainable
let set = new Set()
    .add('APPLE')
    .add('ORANGE')
    .add('MANGO');

// Or we can initialise the Set with an array
let set = new Set(['APPLE', 'ORANGE', 'MANGO']);

// We can check to see if a value is in a set :
set.has('APPLE') // true

// We can delete a value from the set:
set.delete('APPLE')


// We can count the number of entries in the set :
set.size  // 2


// We can empty the entire set with the clear method:
set.clear();
set.size  // 0


// Sets can only store unique values, so adding a value a second time has no effect:

let set = new Set();
set.add('Moo');
set.size
// 1
set.add('Moo');
set.size
// 1


// ***** Looping over a Set ******
// We can use the for-of loop to loop over items in our set

let set = new Set(['APPLE', 'ORANGE', 'MANGO']);
for (let entry of set) {
    console.log(entry);
}
// APPLE
// ORANGE
// MANGO
```

## Promises

....

```typescript
// *** 1. via callbacks ***
// - In ES5 (Asynchronous flow has been handled -via callbacks)

function doAsyncTask(cb) {
  setTimeout(() => {
    console.log("Async Task Calling Callback");
    cb();
  }, 1000);
}

doAsyncTask(() => console.log("Callback Called"));


// *** 2. via callbacks ***
// - In ES6 (Asynchronous flow has been handled -via inbuild Promise API)

var promise = new Promise(
        (resolve, reject) => {}
    );
promise.then(
    (val) => console.log(val),
    (err) => console.error(err)
);

let error = false;
function doAsyncTask() {
  return new Promise((resolve, reject) => {

    setTimeout(() => {

      if (error) {
        reject('error');
      } else {
        resolve('done');
      }

    }, 1000);

  });
}

doAsyncTask().then(
    (val) => console.log(val),  // 'done'
    (err) => console.error(err)
);



// *** 3. Immediately Resolved Promise ***
let promise = Promise.resolve('done');
promise.then((val) => console.log(val)); // 'done'

let promise = Promise.reject('fail');
promise.then(
    (val) => console.log(val),
    (err) => console.error(err)  // 'fail'
);


// *** 4. Handling Errors ***

Promise.resolve("done")
  .then(
    (val) => {
      console.log(val);
      return 'done2';
    },
    (err) => console.error(err)
  )
  .then(
    (val) => console.log(val),
    (err) => console.error(err)
  );
// 'done'
// 'done2'

// -or- (handle err only once in the last then block)
Promise.resolve("done")
  .then(
    (val) => {
      console.log(val);
      return 'done2';
    }
  )
  .then(
    (val) => {
      console.log(val);
      return 'done3';
    }
  );
  .then(
    (val) => console.log(val),
    (err) => console.error(err) // we can handle err only once in the last then block
  );
// 'done'
// 'done2'
// 'done3'


// -or- (using catch blocl)

Promise.resolve('done')
    .then((val) => { throw new Error("fail") })
    .then((val) => console.log(val))
    .catch((err) => console.error(err));
```

## Class & Interface

....

```typescript
// *** 1. Object Orientation in JavaScript ***

/*
- JavaScript has a **prototype-based** object-oriented programming model. 
    - It creates objects using other objects as blueprints 
    - to implement inheritance it manipulates using prototype chain
- In normal programming lang (C++ or Java) object orientation is implemented as Classical OO Pattern

- Although the prototype-pattern is a **valid** way to implement object orientation 
    -it can be confusing for newer javascript developers

- So in ES6 we have an alternative syntax, 
    -that closer matches the classical OO pattern as is seen in other languages

Tip:
- Under the hood the new syntax still uses the prototype pattern with constructor functions and the prototype-chain. 
- However, it provides a more common and 'convenient syntax' with less boilerplate code.

Note:
- TypeScript supports the ES6 class syntax 
- but also adds some other feature like access modifiers and interfaces
*/

class Person { 
    firstName = ""; 
    lastName = "";
    constructor(firstName, lastName) {  
        this.firstName = firstName;
        this.lastName = lastName;
    }

    name() { 
        return `${this.firstName} ${this.lastName}`;
    }

    whoAreYou() {
        return `Hi i'm ${this.name()}`; 
    }
}



// *** Class Instance *** 
/*
- A class is a **blueprint** for creating an object
- that 'created object' is an **instance** of a class
- We instantiate a class by using the **new** keyword and when that happens javascript calls the constructor function. 
- We can pass to the **constructor** arguments which it uses to initialise properties or call other function
*/ 

let asim = new Person("Asim","Hussain");
asim.whoAreYou()  // "Hi i'm Asim Hussain"


// After Transpiled to ES5 (it look like this)

// Person class
var Person = (function () {
    function Person(firstName, lastName) {
        this.firstName = "";
        this.lastName = "";
        this.firstName = firstName;
        this.lastName = lastName;
    }
    Person.prototype.name = function () {
        return this.firstName + " " + this.lastName;
    };
    Person.prototype.whoAreYou = function () {
        return "Hi i'm " + this.name();
    };
    return Person;
}());

// Person class instance
var asim = new Person("Asim", "Hussain");
asim.whoAreYou(); // "Hi i'm Asim Hussain"
```

```typescript
// *** 2. Inheritance ***
/*
- A class can inherit from another class. 
- We can create a class blue-print that extends an existing class blue-print by adding other methods or properties.
*/

// We do this by using the extends keyword

class Student extends Person { 
    course; 

    constructor(firstName, lastName, course) {
        // We use the **super** function to call the constructor of the parent class
        super(firstName, lastName); 
        this.course = course;
    }

    // We can override member functions of the parent class with our own versions
    whoAreYou() {     
        // 'super' refers to the parent instance
        return `${super.whoAreYou()} and i'm studying ${this.course}`; 
    }
}

// instantiate this derived class
let asim = new Student("Asim", "Hussain", "Angular 2");
console.log(asim.whoAreYou());
// Hi i'm Asim Hussain and i'm studying Angular 2



// After Transpiled to ES5 (it look like this)

// extends commoon fn
var __extends = (this && this.__extends) || (function () {
    var extendStatics = Object.setPrototypeOf ||
        ({ __proto__: [] } instanceof Array && function (d, b) { d.__proto__ = b; }) ||
        function (d, b) { for (var p in b) if (b.hasOwnProperty(p)) d[p] = b[p]; };
    return function (d, b) {
        extendStatics(d, b);
        function __() { this.constructor = d; }
        d.prototype = b === null ? Object.create(b) : (__.prototype = b.prototype, new __());
    };
})();


// Person class
var Person = (function () {
    function Person(firstName, lastName) {
        this.firstName = "";
        this.lastName = "";
        this.firstName = firstName;
        this.lastName = lastName;
    }
    Person.prototype.name = function () {
        return this.firstName + " " + this.lastName;
    };
    Person.prototype.whoAreYou = function () {
        return "Hi i'm " + this.name();
    };
    return Person;
}());
var asim = new Person("Asim", "Hussain");
asim.whoAreYou(); // "Hi i'm Asim Hussain"



// Student class
var Student = (function (_super) {
    __extends(Student, _super);
    function Student(firstName, lastName, course) {
        var _this = 
        // We use the **super** function to call the constructor of the parent class
        _super.call(this, firstName, lastName) || this;
        _this.course = course;
        return _this;
    }
    // We can override member functions of the parent class with our own versions
    Student.prototype.whoAreYou = function () {
        // 'super' refers to the parent instance
        return _super.prototype.whoAreYou.call(this) + " and i'm studying " + this.course;
    };
    return Student;
}(Person));


// instantiate this derived class
var asim = new Student("Asim", "Hussain", "Angular 2");
console.log(asim.whoAreYou());




// ----------------------------------- / ES6 (es6 is over) ----------------------------------------------
// Everything we have learned so far about classes is pure ES6 JavaScript.
```

```typescript
// *** 3. Access Modifiers (TypeScript Only) ***

/*
TypeScript adds some nice functionality on top of ES6 classes
    - namely function
    - property visibility via access modifiers
*/


class Person {
    private firstName = "";
    private lastName = "";

    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
}

// And we create a function on our Student class called test() which tries to access one of these properties
class Student extends Person {
  // .
  // .
  // .
  test() {
    console.log(this.firstName);
  }
}

// And we tried to call this function from our Student instance
let asim = new Student("Asim", "Hussain", "Angular 2");
console.log(asim.test());

/*
Compiling the above with typescript compiler throws error:

error TS2341: Property 'firstName' is private and only accessible within class 'Person'.
*/


/*

- By marking the firstName property as **private** it is now only **visible** from one of the methods on Person class.
- We can also define 'class methods' as private with the same effect. 
- If we tried to call a private method from outside of a Person class, the typescript transpiler throws an error.
*/

/*
There are 3 access modifiers:
**public**  (need not to specify)
This is the 'default' and means its visible everywhere.

**private**
Only member functions of the class it’s declared in can see this.

**protected**
- Only Child can See that
- Only the class it’s declared in and any class that inherits from that class can see this.

*/


// ***Constructor shortcut (TypeScript Only) ***

// A really common pattern in constructors is to use them to initialise properties via arguments you pass into the constructor, like in our example:

class Person {
    private firstName = "";
    private lastName = "";

    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
}
// As long as you are using an access modifier TypeScript lets us shorten this to:

class Person {
    constructor(private firstName, private lastName) {
    }
}



// *** 4. Interfaces (TypeScript Only)  ***
/*
- TypeScript has another feature called an interface. An interface can be used in a number of scenarios but by far the most common is when used with classes.

- When used with classes the syntax looks like this:
*/

class Person implements Human {
}

/*
Human in the example above is an interface. 
An interface lets you describe the minimum set of public facing properties or methods that a class has.

Another way interfaces are explained is that they describe a 
 - 'set of rules the class has to follow',
 - a contract it has to adhere to.

So for us a Human interface might look like:
*/


interface Human {
    firstName: string;
    lastName: string;
}

/*
Important Note: 
Since interfaces are all about the public interface of a class 
 - they can’t have access modifiers, 
 - the properties above have to be public.


** Person class should adhere to the contract aggrement 'Human' interafce **

"If the Person class then doesn’t implement at least a firstName and a lastName then typescript throws an error"


error TS2420: Class 'Person' incorrectly implements interface 'Human'. Property 'firstName' is missing in type 'Person'.

*/



// Sometimes in interface, we need 'optional' contract 
// We can append ? to the name of the property or function to mark it as optional

interface Human {
    firstName: string;
    lastName: string;
    name?: Function;
    isLate?(time: Date): Function;
}
```

## Decorators

....

```typescript
// *** 1. Decorators (TypeScript Only) (might be available in ES7) ***

// E.g.
@Component({
    selector: "thingy",
    template: `foo`
})
class MyComponent {
}


// *** 2. Simple no-argument decorator ***

// @course is just a function
// 'target' is the thing the decorator is attached to, 
//      -so for a class it’s going to be the function constructor for that class, the under-the-hood implementation of a class.
// Knowing this we can actually dynamically add a function to our Person class by using the Object.defineProperty function
function course(target) {

    // We use it to add a function called course onto the class it decorates and for now this function just returns the string "Angular 2"
    Object.defineProperty(target.prototype, 'course', {value: () => "Angular 2"})
}


@course
class Person {
    firstName;
    lastName;

    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
}


// We can now call asim.course() and this prints out "Angular 2"

let asim = new Person("Asim", "Hussain");
console.log(asim.course()); // Angular 2





// *** 3. Decorators with arguments ***

//  how do we pass arguments to our decorator, like the way the @Component decorator works?

function Student(config) { // 1
  return function (target) {
    Object.defineProperty(
        target.prototype,
        'course',
        {value: () => config.course} // 2
    )
  }
}

// 1. We pass a config object to the outer Course function.
// 2. Then use that config in the returned inner decorator function.


@Student({
    course: "Angular 2"
})
class Person {
}

// We can now call asim.course() and this prints out "Angular 2"
let asim = new Person("Asim", "Hussain");
console.log(asim.course()); // Angular 2



/*

Summary :
Decorators are a new feature of TypeScript and used throughout the Angular code

With decorators 
    -we can **configure** and **customise** our classes at 'design time'

They are just functions that can be used to add meta-data, properties or functions to the thing they are attached to.

Nice Reference:
https://github.com/jayphelps/core-decorators.js

*/
```

## Modules

....

```typescript
// *** 1. Module Loading ***

/*
- By default javascript doesn’t have a 'module system' like other languages, e.g. Java or Python.

- This means that if you wanted to call a function in some other file
    -you have to remember to explicitly load that file via script tags before you call the function.

- If you tried to use code that you forgot to add via a script tag, then javascript would complain.
*/

/*
This feature was missing in JavaScript
    -so the community developed their own solutions, 
    - such as 'CommonJS' which is used in node.
*/


// *** 2. ES6 Modules ***

/*
ES6 took the best of the existing module systems and introduced this concept on a language level.

Although it’s made it into the ES6 standard
 - it’s up to the javascript engine makers to actually implement it natively and they haven’t… yet.

So until that,
    -we code using the ES6 module syntax in TypeScript
    - typescript transpiles the code in to ES5 it uses the CommonJS (module loading system)


Note : 
We can configure TypeScript to use other module loaders, but the default is CommonJS.

*/

// *** 3. Exporting ***

// utils.ts
function square(x) {
    return Math.pow(x,2)
}

function cow() {
    console.log("Mooooo!!!")
}

// export { square: square, cow: cow };
export { square, cow }; //short form


// *** 4. Importing ***

// script.ts
import { square, cow } from './utils';

square(2);
cow();


/*
Tip
To compile with typescript we need to provide both files on the command line tsc -t ES5 -w utils.ts script.ts
*/



// *** 5. Aliases ***

/*
We may want to import a function with one name 
    -but then use it via another name. 
    - Perhaps to avoid name collisions or more convenient naming
*/


import { square as sqr } from './utils';
sqr(2);

// Or we can import everything in a file :

import * as utils from './utils';
console.log(utils.square(2));
utils.cow();



// *** 6. Alternative export syntax ***
export { square, cow };

// We can also export functions or variables as they are defined by prepended the word export to the front of their declarations:

export function square(x) {
    return Math.pow(x,2)
}



// *** 7. Default exports ***

// If a module defines one export which is the most common, 
// we can take advantage of the default export syntax

export default function square(x) {
    return Math.pow(x,2)
}

// And then when we import it we don’t need to use { }
import square from './utils';


// Or, if we want to import the default export as well as some other exports, we can use:

import square, { cow } from './utils';

/*

Summary
With ES6 modules we finally have a mechanism for letting the language deal with loading of dependant files for us.

This isn’t baked into javascript engines yet. So to solve this problem in Angular we still use the ES6 module loading syntax but leave it to TypeScript to transpile to CommonJS.

*/
```

## Types

....

```typescript
// *** 1. Transpile-time type checking ***

/*
Most common mistakes we make while writing JavaScript code i
    - is to misspell a property or a method name.
We only find out about the mistake / erros --during runtime

Other languages like C++ or Java have something called **type checking**, 
    -during a compilation phase, it first checks for some simple mistakes in the code and raises an error if it finds any.

TypeScripts transpilation mechanism also performs **type checking**,            -however it only works when we tell TypeScript the type of things.
*/

//e.g. in javascript we might write:

let a;
a = 1;   // number (We expected type of the variable remain a number)
a = '2'; // string  (No error)

// Only some functions which expects 'a' as number misbehaves
// we will come to know this misbehavior only 

/*

- But by mistake we assigned a string '2' to a, this doesn’t cause an error in JavaScript.

Only if one of the functions which depends on a starts misbehaving do we even get a clue that something might be wrong.

However with typescript we can clearly state that we want the a variable to always hold a number
*/

let a: number = 1;

// Then if somewhere else in our code we wrote:
a = "1";

// We get this error:
// error TS2322: Type 'string' is not assignable to type 'number'.

// If we take advantage of types in typescript the transpiler will warn us with a transpile-time errors.


// *** 2. Supported Types ***

// ## Basic Types:
let decimal: number = 6;
let done: boolean = false;
let color: string = "blue";


// ## Arrays:
// way1 (using square brackets []):
let list: number[] = [1, 2, 3];
// let list: number[] = [1, 2, '3'];  // error

// way2 (using generics) :
let list: Array<number> = [1, 2, 3];

// ## Functions:
let fun: Function = () => console.log("Hello");
let fun: Function = () => { 
    console.log("Hi");
    console.log("Hello");
};

// we can also define the expected return type of a function
function returnNumber(): number {
  return 1;
}


// ## Enum :  (available in ES6 too)
// - An Enum is a datatype consisting of a set of named values. 
// - The names are usually identifiers that behave as **constants**.

enum Direction {
    Up,
    Down,
    Left,
    Right
}

let go: Direction;
go = Direction.Up;


// ## Class & Interface :

class Person {};
let person: Person;
let people: Person[];


// Any
// - If we don’t know the type of something we can fall back to using any.
// - it doesn’t provide any **type checking** 
//      -but it makes it clear that we intentionally don’t know the type

let notsure: any = 1;
notsure = "hello"; // This is fine since we don't do type checking with any


// Void: 
// void means no type (function will not return anything)

function returnNothing(): void {
  console.log("Moo");
}


function returnNothing(): void {
  console.log("Moo");

  return 'hi'; // 'transpilation-error'
}


// Type Assertion: 
// Sometimes we end up in a situation where we know more than TypeScript about the type of something. 
// In those situations we can use type assertions as a hint to the transpiler about the type of something

let value: any = "Asim Hussain";
let length: number = (<string>value).length;

// (<string>value) lets TypeScript know that we believe the type of value to be string.




// *** 3. Generics ***

// How can we create re-usable bits of code which can still take advantage of typescripts transpile-time type checking?

// example:

class Audio {}
class Video {}
class Link {}
class Text {}

// We have a class called Post which has a content property. 
class Post {
    // 'content' might be an instance of Audio, Video, Link or Text classes.
    content: any;
}
// We could ignore the type of content and just use any like the example above but this doesn’t give us the benefit of type checking.

// We can create seperate AudioPost, VideoPost, LinkPost and TextPost types, (But, That's Bad)
class AudioPost {
    content: Audio;
}

class VideoPost {
    content: Video;
}

class LinkPost {
    content: Link;
}

class TextPost {
    content: Text;
}

/*
But, That's Bad 
    - apart from being verbose and time-consuming 
    - it assumes we know all the content types upfront. 
    - Maybe a consumer later on would like to create a VRPost type.
*/

// With generics we can dynamically generate a new type by passing into the Post type a type variable

class Audio {}
class Video {}
class Link {}
class Text {}

// <T> is the generic syntax
class Post<T> {
    content: T;
}

let videoPost: Post<Video>;

// it can be named anything, <T> is recommended
// If we have multiple, we can use anything to differntiate
class MyPost<A, B> {
    content1: A;
    content2: B;
}

let myVideoPost: MyPost<Video, Text>;


// *** 4. Optional Types ***

// By default we don’t have to add types in TypeScript
let answer;
answer = 42;

// TypeScript won’t perform any type checking for the above and assumes a type of any.
/*
Important
This behaviour is controlled by the { noImplicitAny: false } flag in tsconfig.json. 
- If set to false then TypeScript assumes any for missing types, 
- If set to true then TypeScript throws an error if no type is present. 
*/


// *** 5. Type Inference. ***
// If a variable is declared and initialised on one line 
//  - TypeScript will try to infer, guess, the type of a variable by how it’s declared
let answer = 42;    // TypeScript detected that as number 
answer = "42";      // 'transpilation-error' 

// error TS2322: Type 'string' is not assignable to type 'number'.




// *** 6. Types for external libraries ***

/*
- This is all fine for code that’s written in TypeScript and has types.

- What if you wanted to use code that wasn’t written in TypeScript

- We can use something called an **Ambient Type Definition**.
- This is a file that contains meta-data about the types in another library, a meta-type file.
- This repository (https://github.com/DefinitelyTyped/DefinitelyTyped) contains type definitions for some of the most popular 3rd party javascript libraries.
*/

/*
To use them in a file we simply:-
Download the associated type file, for example jquery.d.ts.
In the typescript file where we want to use the 3rd party library, add this to the top of the file with :
*/

/// <reference path="jquery.d.ts" />
/*

ur code

*/

// *** 6.1 typings ***
/*
There is a easy way to do this using 'typings' command line tool (npm module)

// 1. install typings
npm install -g typings
// 2. initialize typings (creates a typings.json)
typings init
// 3. install type definition files
typings install jquery --save --source dt --global  


This downloads and installs the type definition files to the ./typings folder and conveniently bundles all of the downloaded files into a single file called index.d.ts.

So then to use jQuery with typescript type support we just need to add a reference to index.d.ts to the top the file where we use jQuery.
*/

/// <reference path="./typings/index.d.ts"/>


/*
Summary
With transpile-time type checking TypeScript can help uncover bugs much earlier and faster than if they were to manifest at run-time.

Using types is optional but highly recommended by the Angular team.

If using 3rd party libraries that have already been transpiled into javascript, typescript can still perform transpile-time type checking if we include the type definition file for the library.

*/
```

## Wrapping Up

We covered the core features of ES6 such as let, const, template strings, fat arrow functions; for-of loops, Map and Set; as well as how to deal with asynchronous programming by using Promises.

With TypeScript we covered classes, class access modifiers, interfaces; decorators, modules and types including generic types.

