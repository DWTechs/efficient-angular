---
layout: default
title: Reduce
permalink: /javascript/ecmascript/array/reduce/

---

Previous : [Table of Contents](./index.md)


# Reduce

The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.


## Syntax
```javascript
// Arrow function
reduce((accumulator, currentValue) => { ... } )
reduce((accumulator, currentValue, index) => { ... } )
reduce((accumulator, currentValue, index, array) => { ... } )
reduce((accumulator, currentValue, index, array) => { ... }, initialValue)

// Callback function
reduce(callbackFn)
reduce(callbackFn, initialValue)

// Inline callback function
reduce(function callbackFn(accumulator, currentValue) { ... })
reduce(function callbackFn(accumulator, currentValue, index) { ... })
reduce(function callbackFn(accumulator, currentValue, index, array){ ... })
reduce(function callbackFn(accumulator, currentValue, index, array) { ... }, initialValue)
```

### Reduce parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | A function to execute on each element in the array (except for the first, if no initialValue is supplied). |
| initialValue Optional | A value to use as the first argument to the first call of the callbackFn. If no initialValue is supplied, the first element in the array will be used as the initial accumulator value and skipped as currentValue. Calling reduce() on an empty array without an initialValue will throw a TypeError. |

### CallbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| accumulator | The accumulator accumulates callbackFn's return values. It is the accumulated value previously returned in the last invocation of the callback—or initialValue, if it was supplied (see below). |
| currentValue | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. Starts from index 0 if an initialValue is provided. Otherwise, it starts from index 1. |
| array Optional | The array reduce() was called upon. |


## Return value
The single value that results from the reduction.


## Example
```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15


const getMax = (a, b) => Math.max(a, b);

// callback is invoked for each element in the array starting at index 0
[1, 100].reduce(getMax, 50); // 100
[    50].reduce(getMax, 10); // 50

// callback is invoked once for element at index 1
[1, 100].reduce(getMax);     // 100

// callback is not invoked
[    50].reduce(getMax);     // 50
[      ].reduce(getMax, 1);  // 1

[      ].reduce(getMax);     // TypeError

```