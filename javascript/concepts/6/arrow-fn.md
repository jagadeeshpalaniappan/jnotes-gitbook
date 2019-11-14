# 2. Arrow Fns

* [Arrow functions have no “this”](https://javascript.info/arrow-functions#arrow-functions-have-no-this)
  * 'this' inside arrow fn has no separate scope \(gets from lexical scope\)
    * In normal function, each fn has its own 'this' scope
    * you can solve by using `myFn.bind(this)` or `self`
* [Arrows have no “arguments”](https://javascript.info/arrow-functions#arrows-have-no-arguments)
* Arrow functions can’t run with `new`
  * Because: `No Constructor` and `No Named Fn`
* They also don’t have `super`
* Sytax Sugar



{% embed url="https://medium.com/free-code-camp/learn-es6-the-dope-way-part-ii-arrow-functions-and-the-this-keyword-381ac7a32881" %}

{% embed url="https://www.freecodecamp.org/news/when-and-why-you-should-use-es6-arrow-functions-and-when-you-shouldnt-3d851d7f0b26/" %}

{% embed url="https://javascript.info/arrow-functions" %}





```javascript
/* ES5 */

// normal function

function abc(){
    console.log(`Hello, ES5's function!`);
}
abc();

var abc = function xyz(){
    console.log(`Hello, ES5's function!`);
};
abc();

// named function

var abc = function xyz(){
    console.log(`Hello, ES5's function!`);
}();


// anonymous function
// 1
(function(){
    console.log(`Hello, ES5's IIFE!`);
})();

// 2
(function(){
    console.log(`Hello, ES5's IIFE!`);
}());

// 3

var abc = function(){
    console.log(`Hello, ES5's function!`);
}();


/* ES6 */

// named arrow function
const xyz = () => {
    console.log(`Hello, ES6's Arrow Function!`);
};
xyz();


const xyz = (() => {
    console.log(`Hello, ES6's Arrow Function!`);
})();


// Uncaught SyntaxError: Unexpected token (

/*
const xyz = (() => {
    console.log(`Hello, ES6's Arrow Function!`);
}());
*/

// anonymous arrow function
(() => {
    console.log(`Hello, ES6's Arrow Function!`);
})();
```

