---
description: >-
  push vs pop vs unshift vs shift, splice vs slice, forEach vs filter vs map vs
  reduce, sort
---

# Array Functions

## 1. push vs pop vs unshift vs shift 

```javascript
// Javascript Arrays are objects (stored in a hashtable) close-by m/y location
// { key: index, val: value } // just like regular object

______________________________________________

- push 			// addItemsToEndOfArr
- pop 			// removeItemFromEndOfArr
- unshift 	// addItemsToBeginningOfArr
- shift 		// removeItemFromBeginningOfArr
_______________________________________________

// ----###  push ###----
// Add items to the `end of an array`
// Time Complexity: O(1) // if size exceeds, shifting existing values takes O(n)

const myArr = ['a', 'b', 'c']; myArr.push('d'); // myArr: ['a', 'b', 'c', 'd']
myArr.push('e', 'f', 'g',...); // myArr: ['a', 'b', 'c', 'd', 'e', 'f', 'g']


// ----###  pop ###----
// Remove an item from the `end of an array` // Time Complexity: O(1)

const myArr = ['a', 'b', 'c']; const popedItem = myArr.pop();
// myArr: ['a', 'b']   // popedItem: 'c'

// ----###  unshift ###----
// Add items to the `beginning of an array`
// Time Complexity: O(n) // shiftAllExistingVals // or reAssignAllIndexKeys in obj

const myArr = ['a', 'b', 'c']; myArr.unshift('d'); // myArr: ['d', 'a', 'b', 'c']
myArr.unshift('e', 'f', 'g',...); // myArr: [''e', 'f', 'g', d', 'a', 'b', 'c']

// ----###  shift ###----
// Remove an item from the `beginning of an array`
// Time Complexity: O(n) // shiftAllExistingVals // or reAssignAllIndexKeys

const myArr = ['a', 'b', 'c']; const shiftedItem = myArr.pop();
// myArr: ['b', 'c']   // shiftedItem: 'a'

```



## 2. splice vs slice

```javascript

______________________________________________

- splice 	// insertOrRemoveItems inAnywhereOfArr
- slice		// returns slicedItems fromAnywhereOfArr

// Time Complexity: O(n)
_______________________________________________



// ----###  splice ###----
// Add or Remove items in `anywhere of an array`
// const deletedItems = myArr.splice(startIndex, noOfItemsToRemove)
// modifies the originalArr // can 'add' or 'remove' items from anywhere in the arr

const myArr = ['a', 'b', 'c', 'd', 'e', 'f']; let deletedItems = myArr.splice(2, 3);
// myArr: ['a', 'b', 'f'] // deletedItems: ['c', 'd', 'e']

deletedItems = myArr.splice(2, 0, 'x', 'y', 'z');
// myArr: ['a', 'x', 'y', 'z', 'f'] // deletedItems: ['b']


// ----###  slice ###----
// const newSlicedArr = myArr.slice(startIndex, endIndex)
// returns a new sliced array // does NOT modify the originalArr

const myArr = ['a', 'b', 'c', 'd', 'e', 'f']; const newSlicedArr = myArr.slice(2, 4);
// myArr: ['a', 'b', 'c', 'd', 'e', 'f'] // newSlicedArr: ['c', 'd']

________________________________________________________________________________________________________

```



## 3. forEach vs filter vs map vs reduce

```javascript
______________________________________________

- forEach 	// for...loop iteration
- filter		// returns newFilteredItems
- map				// returns newItems
- reduce		// returns finalResultItem

// Time Complexity: O(n)
_______________________________________________


// ----###  forEach ###----
// myArr.forEach(myFn);	// just for...loop iteration
const oddItems = []; [1,2,3,4,5,6].forEach((item, index) => { item%2 !== 0 && oddItems.push(item) }) // [1, 3, 5]



// ----###  filter ###----
// creates a new filteredItemsArr with all items that pass the test implemented
// const filteredItems = myArr.filter(testFn);

const oddItems = [1,2,3,4,5,6].filter(item => { return item%2 !== 0 } )  // [1, 3, 5]
// `testFn` will return 'true/false' // only 'true' items will be returned as a newArr


// ----###  map ###----
// executes a 'myMapFnImpl' on each item of the array, and add the eachResultItem in-place of actualItem --in a newly created array
// const newTypeItems = myArr.map(myMapFnImpl);

const newItems = [1,2,3,4,5,6].map((item, index) => { return { key: index, val: item }})
// [{'key':0,'val':1},{'key':1,'val':2},{'key':2,'val':3}]
// `mapFn` can change the item into anyType and return // in this eachItem returned as obj { key: index, val: item }


// ----###  reduce ###----
// executes a 'myReducerFnImpl' on each item of the array, resulting in a single output value.
// const finalResultItem = myArr.reduce(myReducerFnImpl, initialVal);

const sum = [1,2,3,4].reduce((res, item)=>{ return res + item; }, 0)
// `myReducerFnImpl` reduce the items into one finalResultItem
```



## 4. sort

```javascript
______________________________________________

- sort 	// sortArrItems using InPlaceAlg

// Time Complexity: O(n logn) // depending on the algorithm chosen by the javascript engine
_______________________________________________

// ----###  sort ###----
// Sorts the items of an array in-place and returns the sortedArr

const sortedItems = myArr.sort(compareFn)
// modifies the originalArr // 'compareFn' is optional -- by default sorts as String

const myArr = ['b', 'c', 'a']; const sortedItems = myArr.sort();
// myArr: ['a', 'b', 'c']; // sortedItems: ['a', 'b', 'c']
[2, 1, 3, 11, 22].sort(); // [1, 11, 2, 22, 3] // by default sort as String
[2, 1, 3, 11, 22].sort((a,b) => a-b); // [1, 2, 3, 11, 22] // using 'compareFn' we can sort any type of items
[2, 1, 3, 11, 22].sort((a, b) => { if (a > b) return 1; else if (b > a) return -1; else return 0; }); // [1, 2, 3, 11, 22]

```

