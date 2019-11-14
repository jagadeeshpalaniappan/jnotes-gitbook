# 1. 'var' vs 'let' vs 'const'

* **var**:  values can be modified later, **`hoisted`**, **`no block scope`**, but it has `function scope`
* **let**: values can be modified later, `not hoisted`, has `block scope`  and `function scope`
* **const**: values can not be modified later, `not hoisted`, has `block scope`  and `function scope`



### var - has 'No Block Scope':

{% tabs %}
{% tab title="Code" %}
```javascript
if (true) {
  var myVar = true; // use "var" instead of "let" for block scope
}

alert(myVar); // true //How? check next tab
```
{% endtab %}

{% tab title="Same Code \(explained with hoisting\)" %}
this is what happened in previous tab code --&gt; hoisting

```javascript
var test;

if (true) {
  test = true; // use "var" instead of "let"
}

alert(test); // true, Now you understood
```
{% endtab %}

{% tab title="use: let \(for block scope\)" %}
```javascript
if (true) {
  let test = true; // use "let"
}

alert(test); // Error: test is not defined
```
{% endtab %}
{% endtabs %}

```javascript
for (var i = 0; i < 10; i++) {
  // ...
}

alert(i); // 10, "i" is visible after loop, it is hoisted
```



### var - has 'Function Scope':

{% tabs %}
{% tab title="Code" %}
```javascript
function sayHi() {
  if (true) {
    var myVar = "Hello";
  }
  alert(myVar); // Hello
}

sayHi();
alert(myVar); // Error: myVar is not defined
```
{% endtab %}

{% tab title="Same Code \(explained with hoisting\)" %}
this is what happened in previous tab code

```javascript
function sayHi() {
  var myVar;
  if (true) {
    myVar = "Hello";
  }
  alert(myVar); // Hello
}

sayHi();
alert(myVar); // Error: myVar is not defined
```
{% endtab %}
{% endtabs %}



**`var`**: function scope, hoisting example

```javascript
var myVar1 = 5;

function myFn() {
  console.log(myVar1);  // undefined (becoz 'myVar1' is hoisted)
  console.log(myVar2);  // ReferenceError: myVar2 is not defined
    
  var myVar1 = 10;
  console.log(myVar1);  // 10
}
myFn();
console.log(myVar1);  // 5
```

**`var`**: function scope, hoisting example

```javascript
var myVar1 = 5;

function myFn() {
  console.log(myVar1);  // 5

  // if u do not declare 'myVar1' inside, 
  // it will try toget it from parent scope
  // if not available in parent scope, 
  // it throws 'ReferenceError: myVar1 is not defined'
  
  // var myVar1 = 10;
  (function () {
    console.log(myVar1);  // 5
  })();

  console.log(myVar1);  // 5
}
myFn();
console.log(myVar1);  // 5
```

**`let`**: block scope

```javascript
function myFn() {

  if (true) {
    let myLet = 'let';
    var myVar = 'var';
  }

  console.log(myVar);  // var
  console.log(myLet);  // ReferenceError: myLet is not defined
}

myFn();

```

How do u make `myVar` as block scope \(like `myLet`\)  without changing `var` --&gt; `let`

```javascript
function myFn() {
  
  (function() {
    if (true) {
      let myLet = 'let';
      var myVar = 'var';
    }
  })();
  
  // Now: myVar is not accessible (bcoz myVar's function scope is ended)
  console.log(myVar);  // ReferenceError: myVar is not defined
  console.log(myLet);
}

myFn();
```

```javascript

function myFn() {
  console.log(myLet);  // ReferenceError: myLet is not defined
  if (true) {
    const myLet = 5;
  }
  console.log(myLet);
}
myFn();
```

**`const`**: block scope

```javascript
function myFn() {

  if (true) {
    const myLet = 5;
    const myConst = 10;
    console.log(myLet);  // 5
    console.log(myConst);  // 10
  }

  console.log(myLet);  // ReferenceError: myLet is not defined
  console.log(myConst);
}
myFn();
```

**`const`**: block scope

```javascript
{
    const myLet = 5;
    const myConst = 10;
    console.log(myLet);  // 5
    console.log(myConst);  // 10
}

console.log(myLet);  // ReferenceError: myLet is not defined
console.log(myConst);
```

**`const`**: re-assignment not allowed

```javascript
let myLet = 5;
const myConst = 10;

myLet = 15;
myConst = 15;	// TypeError: Assignment to constant variable.
```

**`const`**: re-assignment not allowed \(Array and Object values can be changed\) 

But can not assign a new object reference to `myConst`

```javascript
let myLetArr = [1,2,3];
const myConstArr = [1,2,3];
myLetArr.push(4);
myConstArr.push(4);    // allowed (because, it's reference) 
// (only re-assignment is not allowed) (values can be modified)

myLetArr = [1,2];	// works fine
myConstArr = [1,2];	// TypeError: Assignment to constant variable.
```

```javascript
let myLetObj = { key1: 'val1' };
const myConstObj = { key1: 'val1' };

console.log(myLetObj);		// [1,2,3,4]
console.log(myConstObj); // [1,2,3,4]

myLetObj.key2 = 'val2';
myConstObj.key2 = 'val2'; // allowed (because, it's reference) 

myLetObj = { key2: 'val2' }; // works fine
myConstObj = { key2: 'val2' };	// TypeError: Assignment to constant variable.
```

```javascript
const myConst;	// SyntaxError: Missing initializer in const declaration
myConst = 5;
```



Reference:

{% embed url="https://javascript.info/var" %}



