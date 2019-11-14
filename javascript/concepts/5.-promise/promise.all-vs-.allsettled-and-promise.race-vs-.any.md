---
description: Promise.race vs. Promise.any And Promise.all vs. Promise.allSettled
---

# Promise.all vs .allSettled & Promise.race vs .any

{% embed url="https://dev.to/dance2die/promise-race-vs-promise-any-and-promise-all-vs-promise-allsettled-26if" %}



## Promise.race

```javascript
var p1 = new Promise(function(resolve, reject) { 
    setTimeout(() => resolve('one'), 500); 
});
var p2 = new Promise(function(resolve, reject) { 
    setTimeout(() => resolve('two'), 100); 
});

Promise.race([p1, p2])
.then(function(value) {
  console.log(value); // "two"
  // Both fulfill, but p2 is faster
});

var p3 = new Promise(function(resolve, reject) { 
    setTimeout(() => resolve('three'), 100);
});
var p4 = new Promise(function(resolve, reject) { 
    setTimeout(() => reject(new Error('four')), 500); 
});

Promise.race([p3, p4])
.then(function(value) {
  console.log(value); // "three"
  // p3 is faster, so it fulfills
}, function(reason) {
  // Not called
});

var p5 = new Promise(function(resolve, reject) { 
    setTimeout(() => resolve('five'), 500); 
});
var p6 = new Promise(function(resolve, reject) { 
    setTimeout(() => reject(new Error('six')), 100);
});

Promise.race([p5, p6])
.then(function(value) {
  // Not called
}, function(error) {
  console.log(error.message); // "six"
  // p6 is faster, so it rejects
});
```

### Execution Order:

```javascript
// we are passing as argument an array of promises that are already resolved,
// to trigger Promise.race as soon as possible
var resolvedPromisesArray = [Promise.resolve(33), Promise.resolve(44)];

var p = Promise.race(resolvedPromisesArray);
// immediately logging the value of p
console.log(p);

// using setTimeout we can execute code after the stack is empty
setTimeout(function(){
    console.log('the stack is now empty');
    console.log(p);
});

// logs, in order:
// Promise { <state>: "pending" }
// the stack is now empty
// Promise { <state>: "fulfilled", <value>: 33 }
```



```javascript
var foreverPendingPromise = Promise.race([]);
var alreadyFulfilledProm = Promise.resolve(666);

var arr = [foreverPendingPromise, alreadyFulfilledProm, "non-Promise value"];
var arr2 = [foreverPendingPromise, "non-Promise value", Promise.resolve(666)];
var p = Promise.race(arr);
var p2 = Promise.race(arr2);

console.log(p);
console.log(p2);
setTimeout(function(){
    console.log('the stack is now empty');
    console.log(p);
    console.log(p2);
});

// logs, in order:
// Promise { <state>: "pending" } 
// Promise { <state>: "pending" } 
// the stack is now empty
// Promise { <state>: "fulfilled", <value>: 666 }
// Promise { <state>: "fulfilled", <value>: "non-Promise value" }
```

