# 'new' keyword

{% embed url="https://www.freecodecamp.org/news/demystifying-javascripts-new-keyword-874df126184c/" %}



* Every JavaScript function has a `prototype` property, which is empty by default. 
* You can **add functions** to this `prototype` **property**, it is known as a `method`. 



## **Solution3: 'new' and 'this' keywords**

The __**new** operator is used to create an instance of an object which has a `constructor function`.

When we call the constructor function with new, we automate the following actions:

{% hint style="success" %}
1. A **new** object is created
2. It binds '**this'** to the object
3. The constructor function’s prototype object 

    - becomes the \_\_proto\_\_ property of the new object

4. It **returns the object** from the function
{% endhint %}

This is fantastic, because the automation results in less repetitive code!

{% tabs %}
{% tab title="Code" %}
```javascript
function User(name, points) {
 this.name = name; 
 this.points = points;
}
User.prototype.increment = function(){
 this.points++;
}
User.prototype.login = function() {
 console.log("Please login.")
}

let user1 = new User("User 1", 1);
user1.increment();
console.log(user1); // User {name: "User 1", points: 2}
```
{% endtab %}

{% tab title="More Details" %}


```javascript
function User(name, points) {
 this.name = name; 
 this.points = points;
}
User.prototype.increment = function(){
 this.points++;
}
User.prototype.login = function() {
 console.log("Please login.")
}

let user1 = new User("User 1", 1);
user1.increment();
console.log(user1); // User {name: "User 1", points: 2}

let user2 = new User("User 2", 2);
user2.increment();
user2.increment();
console.log(user2); // User {name: "User 2", points: 4}

console.dir(User);
```

![](../../../.gitbook/assets/image%20%28175%29.png)
{% endtab %}
{% endtabs %}



By using the prototype pattern, each method and property is added directly on the object’s prototype.

The interpreter will go up the prototypal chain and find the increment function under the prototype property of User, which itself is also an object with the information inside it. 

Remember — **All functions in JavaScript are also objects**. Now that the interpreter has found what it needs, it can create a new local execution context to run `user1.increment()`.

**`Side note: Difference between __proto__ and prototype`**

* If you are already getting confused about \_\_proto\_\_ and prototype, don’t worry! 
* You are far from the only one to be confused about this.

`prototype` is a **property of the constructor function** that determines what will become the \_\_proto\_\_ property on the constructed object.

So, \_\_proto\_\_ is the reference created, and that reference is known as the prototype chain bond.

## **Solution4: ES6 ‘syntactic sugar’**

Other languages allow us to write our shared methods within the object “constructor” itself. ECMAScript6 introduced the **class** keyword, which allows us to write classes that resemble normal classes of other classical languages. In reality, it is syntactic sugar over JavaScript’s prototypal behavior.

```javascript
class User {
  constructor(name, points) {
    this.name = name;
    this.points = points;
  }
  increment () {
    this.points++;
  }
  login () {
    console.log("Please login.")
  }
}

let user1 = new User("John", 12);
user1.increment();
```

In solution 3, the associated methods were precisely implemented using `User.prototype.functionName`. In this solution 4, the same results are achieved but the syntax looks cleaner.

