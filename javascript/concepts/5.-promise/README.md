# 5. Promise

## Promises, async/await

1. [Introduction: callbacks](https://javascript.info/callbacks)
2. [Promise](https://javascript.info/promise-basics)
3. [`Promises chaining`](https://javascript.info/promise-chaining) `****`
4. [`Error handling with promises`](https://javascript.info/promise-error-handling) `****`
5. [Promise API](https://javascript.info/promise-api)
6. [Promisification](https://javascript.info/promisify)
7. [Microtasks](https://javascript.info/microtask-queue)
8. [`Async/await`](https://javascript.info/async-await)  `***`



{% tabs %}
{% tab title="Promises Chaining" %}
**\#1:**

```javascript
new Promise(function(resolve, reject) {

  setTimeout(() => resolve(1), 1000); // (*)

}).then(function(result) { // (**)

  alert(result); // 1
  return result * 2;

}).then(function(result) { // (***)

  alert(result); // 2
  return result * 2;

}).then(function(result) {

  alert(result); // 4
  return result * 2;

});
```

**\#2:**

```javascript
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve(1), 1000);
});

promise.then(function(result) {
  alert(result); // 1
  return result * 2;
});

promise.then(function(result) {
  alert(result); // 1
  return result * 2;
});

promise.then(function(result) {
  alert(result); // 1
  return result * 2;
});
```

**\#1 & \#2 is not same**

![](../../../.gitbook/assets/image%20%2834%29.png)

* If a `.then` \(or `catch/finally`, doesn’t matter\) handler returns a promise, 
  * the rest of the chain waits until it settles. 
  * When it does, its result \(or error\) is passed further.

```javascript
new Promise(function(resolve, reject) {

  setTimeout(() => resolve(1), 1000);

}).then(function(result) {

  alert(result); // 1

  return new Promise((resolve, reject) => { // (*)
    setTimeout(() => resolve(result * 2), 1000);
  });

}).then(function(result) { // (**)

  alert(result); // 2

  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(result * 2), 1000);
  });

}).then(function(result) {

  alert(result); // 4

});
```
{% endtab %}

{% tab title="Error Handling" %}
* **'promise executor'** and **'promise handlers'** has an "`invisible try..catch`" around it
* **promise executor:** new Promise\(\(resolve, reject\)=&gt; {`...`}\)
* **promise handlers:** 
  * new Promise\(\(resolve, reject\)=&gt; { resolve\(123\); }\).then\(\(\)=&gt;{`...`}\).catch\(\(\)=&gt;{`...`}\)

```javascript

// #1
new Promise((resolve, reject) => {
  throw new Error("Whoops!");
}).catch(alert); // Error: Whoops!

// #2
new Promise((resolve, reject) => {
  reject(new Error("Whoops!"));
}).catch(alert); // Error: Whoops!


// #3
new Promise(function(resolve, reject) {
  setTimeout(() => {
    throw new Error("Whoops!");
  }, 1000);
}).catch(alert);

/*
  - #1 & #2 is same
  - #3 is different // catch block will not execute
  
  - #1: 'promise executor' has "invisible try..catch". it will catch the err and reject(err)
*/

// ------------------------------


// #4
new Promise((resolve, reject) => {
  resolve("ok");
}).then((result) => {
  throw new Error("Whoops!"); // rejects the promise
}).catch(alert); // Error: Whoops!

// #5
new Promise((resolve, reject) => {
  resolve("ok");
}).then((result) => {
  blabla(); // no such function
}).catch(alert); // ReferenceError: blabla is not defined
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

