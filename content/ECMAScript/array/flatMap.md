---
layout: default
title: FlatMap
permalink: /javascript/ecmascript/array/flatmap/

---

Previous : [Table of Contents](./index.md)


# FlatMap

The flatMap() method returns a new array formed by applying a given callback function to each element of the array, and then flattening the result by one level. It is identical to a map() followed by a flat() of depth 1, but slightly more efficient than calling those two methods separately.


## Syntax
```javascript
// Arrow function
flatMap((currentValue) => { ... } )
flatMap((currentValue, index) => { ... } )
flatMap((currentValue, index, array) => { ... } )

// Callback function
flatMap(callbackFn)
flatMap(callbackFn, thisArg)

// Inline callback function
flatMap(function callbackFn(currentValue) { ... })
flatMap(function callbackFn(currentValue, index) { ... })
flatMap(function callbackFn(currentValue, index, array){ ... })
flatMap(function callbackFn(currentValue, index, array) { ... }, thisArg)
```

### FlatMap parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | Function that produces an element of the new Array. |
| thisArg Optional | Value to use as this when executing callback. |

### callbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| element | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. |
| array Optional | The array map was called upon. |


## Return value

A new array with each element being the result of the callback function and flattened to a depth of 1.


## Exemple
```javascript
var arr = [1, 2, 3, 4];

arr.flatMap(x => [x, x * 2]);
// is equivalent to
arr.reduce((acc, x) => acc.concat([x, x * 2]), []);
// [1, 2, 2, 4, 3, 6, 4, 8]


let arr1 = [1, 2, 3, 4];

arr1.map(x => [x * 2]);
// [[2], [4], [6], [8]]

arr1.flatMap(x => [x * 2]);
// [2, 4, 6, 8]

// only one level is flattened
arr1.flatMap(x => [[x * 2]]);
// [[2], [4], [6], [8]]

```