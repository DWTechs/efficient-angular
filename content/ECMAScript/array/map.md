---
layout: default
title: Map
permalink: /javascript/ecmascript/array/map/

---

Previous : [Table of Contents](./index.md)


# Map

The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.

## Syntax
```javascript
// Arrow function
map((element) => { ... } )
map((element, index) => { ... } )
map((element, index, array) => { ... } )

// Callback function
map(callbackFn)
map(callbackFn, thisArg)

// Inline callback function
map(function callbackFn(element) { ... })
map(function callbackFn(element, index) { ... })
map(function callbackFn(element, index, array){ ... })
map(function callbackFn(element, index, array) { ... }, thisArg)
```


### Join parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | Function that is called for every element of arr. Each time callbackFn executes, the returned value is added to newArray. |
| thisAr Optional | Value to use as this when executing callbackFn. |


### Map parameters
| Parameters | Description |
| ---------- | ----------- |
| element | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. |
| array Optional | The array map was called upon. |


## Return value
A new array with each element being the result of the callback function.


## Example
```javascript
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```
