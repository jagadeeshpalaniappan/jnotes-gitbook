# 2. Arrow Fns

* [Arrow functions have no “this”](https://javascript.info/arrow-functions#arrow-functions-have-no-this)
  * 'this' inside arrow fn has no separate scope \(gets from lexical scope\)
    * In normal function, each fn has its own 'this' scope
    * you can solve by using `myFn.bind(this)` or `self`
* [Arrows have no “arguments”](https://javascript.info/arrow-functions#arrows-have-no-arguments)
* Arrow functions can’t run with `new`
  * Because: `No Constructor` and `No Named Fn`
* They also don’t have `super`
* Syntax Sugar

{% embed url="https://medium.com/free-code-camp/learn-es6-the-dope-way-part-ii-arrow-functions-and-the-this-keyword-381ac7a32881" caption="" %}

{% embed url="https://www.freecodecamp.org/news/when-and-why-you-should-use-es6-arrow-functions-and-when-you-shouldnt-3d851d7f0b26/" caption="" %}

{% embed url="https://javascript.info/arrow-functions" caption="" %}

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



## When you should use arrowFn?

{% tabs %}
{% tab title="1. Binding \'this\'  \(obj\)" %}
```javascript
// ############### ES5 (not working) ###############
var obj = {
  id: 5,
  counter: function counter() {
    
    conosle.log(this.id); // 5
    
    setTimeout(function() {
      console.log(this.id);  // undefined // NOT-WORKING
    }.bind(this), 1000);
  }
};


// ############### ES6 (working) ###############
var obj = {
  id: 5,
  counter: function () {
  
    conosle.log(this.id); // 5
    
    setTimeout(() => {
      console.log(this.id); // 5  // WORKING
    }, 1000);
    
  }
};


// ############### ES5 (working) ###############
var obj = {
  id: 5,
  counter: function counter() {
    
    conosle.log(this.id); // 5
    
    setTimeout(function() {
      console.log(this.id);  // 5  // WORKING
    }.bind(this), 1000);
    
  }
};

```
{% endtab %}

{% tab title="2. Binding \'this\' \(forEach\)" %}
```javascript
// ############### ES5 (not working) ###############
var obj = {
  name: 'Jag',
  tasks: ['eat', 'sleep', 'code'],
  runTasks: function() {
  
    console.log(this.name);  // Jag
    
    this.tasks.forEach(function (task) {
      console.log(this.name + " wants to " + task); // normalFn has seperate 'this' scope 
    });
    
  }
};


bunny.showTasks();
// Jag
// [object Window] wants to eat
// [object Window] wants to sleep
// [object Window] wants to code


// ############### ES6 (working) ###############

var obj = {
  name: 'Jag',
  tasks: ['eat', 'sleep', 'code'],
  runTasks: function() {
  
    console.log(this.name);  // Jag
    
    this.tasks.forEach((task) => {
      console.log(this.name + " wants to " + task); // arrowlFn has uses 'this' scope from parent // lexicalScope
    });
    
  }
};

// Jag
// Jag wants to eat
// Jag wants to sleep
// Jag wants to code

// ############### ES5 (working) ###############

var obj = {
  name: 'Jag',
  tasks: ['eat', 'sleep', 'code'],
  runTasks: function() {
  
    console.log(this.name);  // Jag
    
    this.tasks.forEach(function (task) {
      console.log(this.name + " wants to " + task);
    }.bind(this));  // asking the normalFn to use parentFn 'this' scope
    
  }
};

// Jag
// Jag wants to eat
// Jag wants to sleep
// Jag wants to code
```
{% endtab %}
{% endtabs %}

## When you should NOT use arrowFn?

{% tabs %}
{% tab title="1. Object methods" %}
```javascript
// ############### ES6 (not working) ###############

var obj = {
  name: 'Jag',
  setNewName: (newName) => {
    this.name = newName;
  }
}

obj.setNewName('Jagdeesh')
console.log(obj.name) // Jag


// ############### ES5 (working) ###############
var obj = {
  name: 'Jag',
  setNewName: function (newName) {
    this.name = newName;
  }
}

obj.setNewName('Jagdeesh')
console.log(obj.name) // Jagadeesh
```
{% endtab %}

{% tab title="2. Dynamic \'this\' context" %}
```javascript

// If you need your context to be dynamic, 
// arrow functions are not the right choice. 

// Take a look at this event handler below:

// ############### ES6 (not working) ###############

var button = document.getElementById('press');
button.addEventListener('click', () => {
  this.classList.toggle('on'); // TypeError // 'this' is not bound to the button
});


// ############### ES5 (working) ###############

var button = document.getElementById('press');
button.addEventListener('click', function () {
  this.classList.toggle('on'); // TypeError // 'this' is not bound to the button
});

```
{% endtab %}

{% tab title="3. cannotNameFn" %}
```fsharp
It is important to note that arrow functions are anonymous, which means that they are not named.

This anonymity creates some issues:

# 1. Harder to debug
When you get an error, you will not be able to trace the name of the function or the exact line number where it occurred.

# 2. No self-referencing
If your function needs to have a self-reference at any point (e.g. recursion, event handler that needs to unbind), it will not work.
```
{% endtab %}
{% endtabs %}

