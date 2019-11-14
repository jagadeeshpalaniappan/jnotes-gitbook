# LexicalScope vs Closure Scope

LexicalScope ---&gt; **Compile Time** Scope

## Lexical Scope

Consider the following:

```javascript
function init() {
  var name = 'Mozilla'; // name is a local variable created by init
  function displayName() { // displayName() is the inner function, a closure
    alert(name); // use variable declared in the parent function
  }
  displayName();
}
init();
```

* `init()` creates a local variable called `name` and a function called `displayName()`. 
* The `displayName()` function is an inner function that is defined inside `init()` and is only available within the body of the `init()` function. 
* Note that the `displayName()` function has no local variables of its own. 
* However, since inner functions have access to the variables of outer functions, `displayName()` can access the variable `name` declared in the parent function, `init()`.
* * Running the code and notice that the `alert()` statement within the `displayName()` function successfully displays the value of the `name` variable, which is declared in its parent function. 
* This is an example of _**lexical**_ ****_**scoping**_, which describes how a parser resolves variable names when functions are nested. 



* The word **"lexical"** refers to the fact that lexical scoping _**uses the location where a 'variable' is declared**_  within the source code to determine where that variable is available. 
* Nested functions have access to variables declared in their outer scope.



## Closure Scope

Now consider the following example:

```javascript
function makeFunc() {
  var name = 'Mozilla';
  function displayName() {
    alert(name);
  }
  return displayName;
}

var myFunc = makeFunc();
myFunc();
```

Running this code has exactly the same effect as the previous example of the `init()` function above; 

what's different — and interesting — is that 

* the `displayName()` inner function is returned from the outer function before being executed.

At first glance, it may seem unintuitive that this code still works. In some programming languages, the local variables within a function exist only for the duration of that function's execution. Once `makeFunc()` has finished executing, you might expect that the name variable would no longer be accessible. However, because the code still works as expected, this is obviously not the case in JavaScript.

The reason is that functions in JavaScript form closures. A _closure_ is the combination of a function and the lexical environment within which that function was declared. This environment consists of any local variables that were in-scope at the time the closure was created. In this case, `myFunc` is a reference to the instance of the function `displayName` created when `makeFunc` is run. The instance of `displayName` maintains a reference to its lexical environment, within which the variable `name` exists. For this reason, when `myFunc` is invoked, the variable `name` remains available for use and "Mozilla" is passed to `alert`.

Here's a slightly more interesting example — a `makeAdder` function:

```javascript
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12
```

In this example, we have defined a function `makeAdder(x)`, which takes a single argument, `x`, and returns a new function. The function it returns takes a single argument, `y`, and returns the sum of `x` and `y`.

In essence, `makeAdder` is a function factory — it creates functions which can add a specific value to their argument. In the above example we use our function factory to create two new functions — one that adds 5 to its argument, and one that adds 10.

`add5` and `add10` are both closures. They share the same function body definition, but store different lexical environments. In `add5`'s lexical environment, `x` is 5, while in the lexical environment for `add10`, `x` is 10.

