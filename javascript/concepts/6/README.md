# 6. ES6

## ES6 Features:

```javascript
// ES6 Top Features:
1. let and const (Block-Scoped Variables)
2. Arrow Functions                // myArr.map(item => 'new-'+item);

3. Default Parameters             // function myFn(name = 'Jag') { ... } // myFn(); myFn('Jagadeesh')
4. Rest and Spread Parameters     // function myFn(arg1, arg2, ...restArgs) { ... } // myFn(...myArr)
5. Destructuring Assignment       // var { id, name, age } = user;
6. for..of Loop

6. Promises
7. Async / Await

8. Classes
9. Modules
    
11. Template Literals             // var line1 = `My name is ${name} age is ${age}.`;
12. Multi-line Strings
13. Enhanced Object Literals

    
// ES6 Additional Features
1. New Math, Number, String, Array and Object methods
2. Binary and Octal number types
3. Symbols
4. Tail calls
5. Generators & Iterators
6. New data structures like Map and Set
```

![](../../../.gitbook/assets/image%20%2865%29.png)

## JavaScript History

* **1995:** JavaScript is born as LiveScript at Netscape
* **1997:** ECMAScript standard is established by the European Computer Manufacturers Association
* **1999:** ES3 comes out and IE5 is all the rage
* **2000–2005:** _XMLHttpRequest_, a.k.a. AJAX, gains popularity in apps such as Outlook Web Access \(2000\) and Oddpost \(2002\), Gmail \(2004\) and Google Maps \(2005\)
* **2009:** ES5 comes out \(this is what most of us use now\) with _forEach, Object.keys, Object.create_ \(specially for [Douglas Crockford](http://www.crockford.com/)\), and standard JSON
* * **2015:** ES6/ECMAScript2015 comes out fixing a lot of problematic parts of ES5
* **2016:** ES7 is on the horizon

## 1. let and const \(Block-Scoped Variables\)

...

## 2. Arrow Functions in ES6

{% embed url="https://jagadeeshpalaniappan.gitbook.io/jnotes/javascript/concepts/6/arrow-fn" %}

{% tabs %}
{% tab title="JS" %}
```javascript
var logUpperCase = function() {
  var self = this;

  this.string = this.string.toUpperCase()
  return function () {
    return console.log(self.string)
  }
}

logUpperCase.call({ string: 'es6 rocks' })()
```
{% endtab %}

{% tab title="ES6" %}
```javascript
var logUpperCase = function() {
  this.string = this.string.toUpperCase()
  return () => console.log(this.string)
}

logUpperCase.call({ string: 'es6 rocks' })()

```
{% endtab %}
{% endtabs %}

....

{% tabs %}
{% tab title="JS" %}
```javascript
var ids = ['ONE', 'TWO'];
var messages = ids.map(function (value, index, list) {
  return 'ID of ' + index + ' element is ' + value + ' ' // explicit return
});
```
{% endtab %}

{% tab title="ES6" %}
```javascript
var ids = ['ONE','TWO']
var messages = ids.map((value, index, list) => `ID of ${index} element is ${value} `) // implicit return
```
{% endtab %}
{% endtabs %}



## 3.Default Parameters

{% tabs %}
{% tab title="JS" %}
```javascript
var getAccounts = function(limit) {
  var limit = limit || 10
  //...
}

var link = function (height, color, url) {
    var height = height || 50
    var color = color || 'red'
    var url = url || 'http://capitalone.io'
    //...
}
```
{% endtab %}

{% tab title="ES6" %}
In ES6, we can put the default values right in the signature of the functions like so:

```javascript
var getAccounts = function(limit = 10) {
  //...
}
var link = function(height = 50, color = 'red', url = 'http://capitalone.io') {
  //...
}
```
{% endtab %}
{% endtabs %}

## 4. Rest and Spread Parameters in ES6

### Rest Parameters 

{% tabs %}
{% tab title="JS" %}
If you have ever used unlimited number of arguments, then you know the _**argument**_ object. _**argument**_ object contains all parameters passed to the function. The problem is that this _arguments_ object is not a real array. You have to convert it to an array if you want to use functions like _sort_ or _map_ explicitly. For example, this request function converts _arguments_ using _call\(\)_:

```javascript
function request(url, options, callback){
  var args = Array.prototype.slice.call(arguments, f.length);
  var url = args[0]
  var callback = args[2]
  // …
}
```
{% endtab %}

{% tab title="ES6" %}
So is there a better way in ES6 to access an indefinite number of arguments as an array? Yes! It’s rest parameters syntax 

```javascript
function(url, options, ...callbacks) {
  var callback1 = callbacks[0];
  var callback2 = callbacks[2];
  // ...
}
```

Note: In the rest array, the first parameter is the one that doesn’t have a name, e.g., the callback is at index 0, not 2 as in ES5's _arguments_. Also, putting other named arguments after the rest parameter will cause a **syntax error**. The rest parameter is a great sugarcoating addition to JavaScript since it replaces the _arguments_ object, which wasn’t a real array.
{% endtab %}
{% endtabs %}

### Spread Parameters 

{% tabs %}
{% tab title="JS" %}
In ES5, if you wanted to use an array as an argument to a function, you would have to use the _apply\(\)_ function:

```javascript
function request(url, options, callback) { 
  // ...
}
var arrArgs = ['http://capitalone.io', {...}, function(){...}]
request.apply(null, arrArgs)
```
{% endtab %}

{% tab title="ES6" %}
Now in ES6, we can use the spread parameters which look similar to the rest parameters in syntax as they use ellipses…:

```javascript
function request(url, options, callback) { 
  // ...
}
var arrArgs = ['http://capitalone.io', {...}, function(){...}]
request(...arrArgs)
```
{% endtab %}
{% endtabs %}

ES6 Developers can use the spread operator in the following cases:

* Function calls as seen above
* Array literals, e.g., `array2 = […array1, x, y, z]`
* Destructuring \(section 5 of this essay\)
* new function calls \(constructors\), e.g., `var d = new Date(…dates)`
* push\(\) calls, e.g., `arr1.push(…arr2)`

The spread operator has a similar syntax to the rest parameters, but rest is used in the function definition/declaration and spread is used in the calls and literals.

## 5. Destructuring Assignment

{% tabs %}
{% tab title="JS" %}
```javascript
var data = $('body').data(); // data has properties userId and accountNumber   
var userId = data.userId;
var accountNumber = data.accountNumber;

//------

var json = require('body-parser').json

//------

var body = req.body; // body has username and password
var username = body.username;
var password = body.password;

//------
var myArr = [ 1, 2, 3, 4, 5 ];
var one = myArr[0];
var two = myArr[1];
var three = myArr[2];
```
{% endtab %}

{% tab title="ES6" %}
```javascript
var { userId, accountNumber} = $('body').data() 

//------

var {json} = require('body-parser')

//------

var {username, password} = req.body

//------

var [one, two, three] = [ 1, 2, 3, 4, 5 ];

```
{% endtab %}
{% endtabs %}

## 6. for..of Loop

{% embed url="https://thecodebarbarian.com/for-vs-for-each-vs-for-in-vs-for-of-in-javascript" %}

## 6. Promises

....

## 7. Async / Await

....

## 8. Classes

{% tabs %}
{% tab title="JS" %}
...TODO...
{% endtab %}

{% tab title="ES6" %}
```javascript
class BaseModel {
  constructor(options = {}, data = []) { // class constructor
        this.name = 'Base';
        this.url = 'http://azat.co/api';
        this.data = data;
        this.options = options;
    }

    getName() { // class method
        console.log(`Class name: ${this.name}`)
    }
}
```

```javascript
class AccountModel extends BaseModel {
    constructor(options, data) {
        super({private: true}, ['32113123123', '524214691']) // Call the parent method with super
        this.name = 'Account Model'
        this.url +='/accounts/'
    }

    // you can also set up a getter like this with accountsData as a property:
    get accountsData() { // Calculated attribute getter
      // ... make XHR
     return this.data
    }
}
```

```javascript
let accounts = new AccountModel(5)
accounts.getName(); // Class name: Account Model
console.log('Data is %s', accounts.accountsData) //Data is %s 32113123123,524214691
```
{% endtab %}
{% endtabs %}

## 9. Modules

* As you may know, there was no native modules support in JavaScript before ES6. 
* People came up with AMD, RequireJS, CommonJS and other workarounds 
* With **ES6** there are now **built-in modules** with _**import**_ and _**export**_ operands.

{% tabs %}
{% tab title="JS" %}


Let’s say we have _port_ variable and _getAccounts_ method in ES5 **`'module.js'`**

```javascript
module.exports = {
  port: 3000,
  getAccounts: function() {
    //...
  }
}
```

In ES5 _**`'main.js'`**_, we would `require(`_`‘module’`_`)` that dependency:

```javascript
var service = require('module.js')
console.log(service.port) // 3000
```
{% endtab %}

{% tab title="ES6" %}
In ES6, we would use _export_ and _import_. For example,  _**`'module.js'`** file_:

```javascript
export var port = 3000
export function getAccounts(url) {
  ...
}
```

In the importer ES6 file _**`'main.js',`**'_

```javascript
import {port, getAccounts} from 'module'
console.log(port) // 3000
```

Or we can import everything as a variable _service_ in _main.js_:

```javascript
import * as service from 'module'
console.log(service.port) // 3000
```

Note, that **`native support for ES6 modules in browsers is not coming any time soon`** 

\(as of this writing at least\), so you’ll need something like [jspm](http://jspm.io/) to utilize ES6 modules.
{% endtab %}
{% endtabs %}



{% embed url="https://thecodebarbarian.com/for-vs-for-each-vs-for-in-vs-for-of-in-javascript" %}

## 11. Template Literals

{% tabs %}
{% tab title="JS" %}
```javascript
var name = 'Your name is ' + first + ' ' + last + '.'
var url = 'http://localhost:3000/api/messages/' + id
```
{% endtab %}

{% tab title="ES6" %}
```javascript
var name = `Your name is ${first} ${last}.`
var url = `http://localhost:3000/api/messages/${id}`
```

This is neat and allows developers to see the end result of the strings at one glance instead of trying to evaluate the concatenation expression.
{% endtab %}
{% endtabs %}

### Multi-line is possible

{% tabs %}
{% tab title="JS" %}
```javascript
var roadPoem = 'Then took the other, as just as fair,\n\t'
    + 'And having perhaps the better claim\n\t'
    + 'Because it was grassy and wanted wear,\n\t'
    + 'Though as for that the passing there\n\t'
    + 'Had worn them really about the same,\n\t'
```
{% endtab %}

{% tab title="ES6" %}
While in ES6, simply utilize the backticks as follows:

```javascript
var roadPoem = `Then took the other, as just as fair,
    And having perhaps the better claim
    Because it was grassy and wanted wear,
    Though as for that the passing there
    Had worn them really about the same,`

var fourAgreements = `You have the right to be you.
    You can only be you when you do your best.`
```
{% endtab %}
{% endtabs %}

### Tagged Templates

Tagged templates is another use case for Template Literals. A tagged template is a function call that uses a template literal from which to get its arguments.

```javascript
function greet(strArr, nameArg, ageArg) {
  console.log(strArr);  // ["My name is ", " and age is ", " years old."]
  console.log(nameArg); // Jagadeesh
  console.log(ageArg);  // 22
  
  const finalResp = 'Hello, ' + strArr[0] + nameArg + strArr[1] + ageArg;
  return finalResp;
}

var name = 'Jagadeesh';
var age = 22;

// Tagged Templates:
greet `My name is ${name} and age is ${age} years old.`  // Hello, My name is Jagadeesh and age is 22

// Equivalent old fn:
greet(["My name is ", " and age is ", " years old."], name, age); // Hello, My name is Jagadeesh and age is 22

```

## 13. Enhanced Object Literals

....



## Additional Resources:

[https://medium.com/capital-one-tech/my-12-favorite-es6-es2015-features-76e70397fee0](https://medium.com/capital-one-tech/my-12-favorite-es6-es2015-features-76e70397fee0)

1. [ES6/ES2015 Cheatsheet](https://github.com/azat-co/cheatsheets/tree/master/es6)
2. [_Understanding ECMAScript 6_ by Nicolas Zakas book](https://leanpub.com/understandinges6)
3. [_Exploring ES6_ by Dr. Axel Rauschmayer](https://leanpub.com/exploring-es6)

