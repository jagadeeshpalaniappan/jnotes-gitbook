# Function vs Object vs Array

* **In JavaScript everything is an** _**'object'**_ 
  * except
    * `primitive data types:` \(boolean, number and string\),
    * and `undefined` 
  * even `null` is also considered as an **object**  `typeof null // "object"`

{% hint style="warning" %}
* In JavaScript, **function** is also an _**object  \(Function Object\)**_
  * additionally it has a **constructor**
  * has other properties like Object
{% endhint %}

## Function vs Object vs Array

{% tabs %}
{% tab title="Function" %}
```javascript
function myFn() {
   this.prop1 = 1; 
}

myFn();                       // works fine
console.log(typeof myFn);     // function
console.dir(myFn);
```

![](../../../.gitbook/assets/image%20%2884%29.png)

```javascript
const f1 = new myFn();        // works fine
// f1()                       // TypeError: myObj is not a function

console.dir(f1);
```

`f1` is an object

![](../../../.gitbook/assets/image%20%28204%29.png)

Function Expression also behaves the same way
{% endtab %}

{% tab title="Object" %}


```javascript
var myObj = { prop1: 1 };

// myObj();       // TypeError: myObj is not a function
// new myObj();   // TypeError: myObj is not a constructor
console.log(typeof myObj);    // object
console.dir(myObj);
```



![](../../../.gitbook/assets/image%20%28162%29.png)
{% endtab %}

{% tab title="Array" %}
```javascript
var myArr = [ 1, 2, 3 ];
// myArr();       // TypeError: myArr is not a function
// new myArr();   // TypeError: myArr is not a constructor
console.log(typeof myArr);    // object
console.dir(myArr);
```

![](../../../.gitbook/assets/image%20%2852%29.png)

```javascript
myArr['prop1'] = "Hello"
console.log(myArr); // [1, 2, 3, prop1: "Hello"]
console.dir(myArr);
```

![](../../../.gitbook/assets/image%20%2857%29.png)
{% endtab %}
{% endtabs %}

![](https://cdn-media-1.freecodecamp.org/images/CHrqNxf5I7tIo4-CfbSXqC6fnDd2H273ieWJ)



