---
description: Function Declaration vs Function Expression vs Function Constructor
---

# Named Function vs Anonymous Function

## Named Function vs Anonymous Function

### 1.Difference in Hoisting

* '**function' declarations** are --&gt; [Hoisted](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)  \(hoisted as `fn` itself\)
* **'variable' declarations** are also --&gt; [Hoisted](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)  \(but hoisted as `undefiend`\)

{% tabs %}
{% tab title="Code" %}
```javascript
// -------------------------- CHECK: HOISTING  --------------------------

myNamedFn('Jagadeesh'); // TypeError: myAnonymousFn is not a function
// myAnonymousFn('Jagadeesh'); // TypeError: myAnonymousFn is not a function
// myArrowFn('Jagadeesh'); // TypeError: myArrowFn is not a function
// myAnonymousNamedFn('Jagadeesh'); // TypeError: myAnonymousNamedFn is not a function
// myNamedFn2('Jagadeesh'); // ReferenceError: myNamedFn2 is not defined

// -------------------------- / CHECK: HOISTING  --------------------------

var myVar = 123;

function myNamedFn(name) {
  console.log('Hello! ' + name);
}

var myAnonymousFn = function(name) {
  console.log('Hello! ' + name);
};

var myArrowFn = (name) => {
  console.log('Hello! ' + name);
}

var myAnonymousNamedFn = function myNamedFn2(name) {
  console.log('Hello! ' + name);
};


myNamedFn('Jagadeesh'); // Hello! Jagadeesh
myAnonymousFn('Jagadeesh'); // Hello! Jagadeesh
myArrowFn('Jagadeesh'); // Hello! Jagadeesh
myAnonymousNamedFn('Jagadeesh'); // Hello! Jagadeesh

// myNamedFn2('Jagadeesh'); // ReferenceError: myNamedFn2 is not defined
```
{% endtab %}

{% tab title="Explanation" %}
```javascript
// -------------------------- CHECK: HOISTING  --------------------------

myNamedFn('Jagadeesh'); // Hello (updated)! Jagadeesh
// myAnonymousFn('Jagadeesh'); // TypeError: myAnonymousFn is not a function
// myArrowFn('Jagadeesh'); // TypeError: myArrowFn is not a function
// myAnonymousNamedFn('Jagadeesh'); // TypeError: myAnonymousNamedFn is not a function
// myNamedFn2('Jagadeesh'); // ReferenceError: myNamedFn2 is not defined



console.log(myVar); // undefined
console.log(myNamedFn); // ƒ myNamedFn(name) { console.log('Hello! ' + name) }
console.log(myAnonymousFn); // undefined
console.log(myArrowFn); // undefined
console.log(myAnonymousNamedFn); // undefined
// console.log(myNamedFn2); // ReferenceError: myNamedFn2 is not defined

// -------------------------- / CHECK: HOISTING  --------------------------


var myVar = 123;

// 'myNamedFn' is hoisted as a 'fn'
function myNamedFn(name) {
  console.log('Hello! ' + name);
}

// 'myAnonymousFn' is hoisted as 'undefined'
var myAnonymousFn = function(name) {
  console.log('Hello! ' + name);
};

// 'myArrowFn' is hoisted as 'undefined'
var myArrowFn = (name) => {
  console.log('Hello! ' + name);
}

// 'myAnonymousNamedFn' is hoisted as 'undefined'
// 'myNamedFn2' is NOT defined itself 
var myAnonymousNamedFn = function myNamedFn2(name) {
  console.log('Hello! ' + name);
};


// 'myNamedFn' is hoisted as a 'fn'
// myNamedFn is updated with with new function and hoisted
function myNamedFn(name) {
  console.log('Hello (updated)! ' + name);
}


console.log(myVar); // 123
myNamedFn('Jagadeesh'); // Hello (updated)! Jagadeesh
myAnonymousFn('Jagadeesh'); // Hello! Jagadeesh
myArrowFn('Jagadeesh'); // Hello! Jagadeesh
myAnonymousNamedFn('Jagadeesh'); // Hello! Jagadeesh

// myNamedFn2('Jagadeesh'); // ReferenceError: myNamedFn2 is not defined
```
{% endtab %}

{% tab title="More \(with const & let\)" %}
```javascript
// -------------------------- CHECK: HOISTING  --------------------------

myNamedFn('Jagadeesh'); // Hello (updated)! Jagadeesh
// myAnonymousFn('Jagadeesh'); // TypeError: myAnonymousFn is not a function
// myConstAnonymousFn('Jagadeesh'); // ReferenceError: Cannot access 'myConstAnonymousFn' before initialization
// myLetAnonymousFn('Jagadeesh'); // ReferenceError: Cannot access 'myLetAnonymousFn' before initialization


console.log(myVar); // undefined
console.log(myConst); // undefined
console.log(myLet); // undefined

console.log(myNamedFn); // ƒ myNamedFn(name) { console.log('Hello! ' + name) }
console.log(myAnonymousFn); // undefined
// console.log(myConstAnonymousFn); // ReferenceError: Cannot access 'myConstAnonymousFn' before initialization
// console.log(myLetAnonymousFn); // ReferenceError: Cannot access 'myLetAnonymousFn' before initialization

// -------------------------- / CHECK: HOISTING  --------------------------


var myVar = 123;
const myConst = 123;
let myLet = 123;

// 'myNamedFn' is hoisted as a 'fn'
function myNamedFn(name) {
  console.log('Hello! ' + name);
}

// 'myAnonymousFn' is hoisted as 'undefined'
var myAnonymousFn = function(name) {
  console.log('Hello! ' + name);
};


const myConstAnonymousFn = function(name) {
  console.log('Hello! ' + name);
};

// 'myAnonymousFn' is hoisted as 'undefined'
let myLetAnonymousFn = function(name) {
  console.log('Hello! ' + name);
};



console.log(myVar); // 123
myNamedFn('Jagadeesh'); // Hello! Jagadeesh
myAnonymousFn('Jagadeesh'); // Hello! Jagadeesh
myConstAnonymousFn('Jagadeesh'); // Hello! Jagadeesh
myLetAnonymousFn('Jagadeesh'); // Hello! Jagadeesh

```
{% endtab %}
{% endtabs %}

### 2. Better Debugging

#### IIFE

One of the more famous use cases for anonymous functions are Immediately Invokable Function Expressions \(IIFE\). IIFE, for short, is a pattern that uses an anonymous function which immediately creates and invokes the contents of the function.

```javascript
// IIFE (Immediately Invokable Function Expression)
(function() {
  console.log('iife'); // iife
})();
```

* Consider the case where there is an **error down the path but it is clouded by anonymous functions**. 
* The call stack \(as evidenced below\) is all labelled as anonymous giving the developer no hope in tracing the error without scouring all the files of the project.

![](https://media.licdn.com/dms/image/C4E12AQELf_WmgcYJKA/article-inline_image-shrink_1500_2232/0?e=1574899200&v=beta&t=OHcEPGzyJ9BP7k6YHBtKB7tyxwWFstya5-f0m2PXT3I)

* What about anonymous functions with names? 
* Yes while it is commonly created without a name, anonymous functions can be created with a name.

```javascript
var someOtherFunctionName = function accio(name) {
  if (someCondn) { accio(name) }
  console.log(name + ' Potter!');
}
```

* The benefit of doing so is that you could use the function name in recursive situations as well as **having the function name in your call stack for easier debugging**. 
* Anonymous functions are a **convenience feature of the language** that allows you to create functions without requiring a name but it is commonly becoming [good practice](http://jscs.info/rule/disallowAnonymousFunctions) to name-all-functions for a better developer debugging \(and development\) experience.

![](https://media.licdn.com/dms/image/C4E12AQGTL397NQPIAA/article-inline_image-shrink_1000_1488/0?e=1574899200&v=beta&t=JxUNEMSPDuOj-MqHIcYPC4lWWuAYxpodVBCk-mUjFDI)



