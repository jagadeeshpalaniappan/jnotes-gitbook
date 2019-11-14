# 4. Function

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

* There are no classes in JavaScript. 
* Instead functions in JavaScript may be made to behave like constructors 

  * by preceding a function call with the `new` keyword. 
  * This is known as the [constructor pattern](http://aaditmshah.github.io/why-prototypal-inheritance-matters/#constructors_vs_prototypes).

* Hence a function can be used in place of an object. 
* Similarly arrays are also objects in JavaScript. 

  * On the other hand objects can be thought of as associative arrays.

{% hint style="info" %}
Since there are no classes in JavaScript. JavaScript is a 'prototypal object oriented language'. 

* This means that objects in JavaScript directly inherit from other objects. 
* Hence we don't need classes. 
* All we need is a way to create and extend objects.
{% endhint %}

Read the following thread to learn more about prototypal inheritance in JavaScript: [Benefits of prototypal inheritance over classical?](https://stackoverflow.com/q/2800964/783743)

