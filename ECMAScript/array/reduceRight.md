---
layout: default
title: ReduceRight
permalink: /javascript/ecmascript/array/reduceright/

---

Previous : [Table of Contents](./index.md)


# ReduceRight

The reduceRight() method applies a function against an accumulator and each value of the array (from right-to-left) to reduce it to a single value.


## Syntax
```javascript
// Arrow function
reduceRight((accumulator, currentValue) => { ... } )
reduceRight((accumulator, currentValue, index) => { ... } )
reduceRight((accumulator, currentValue, index, array) => { ... } )
reduceRight((accumulator, currentValue, index, array) => { ... }, initialValue)

// Callback function
reduceRight(callbackFn)
reduceRight(callbackFn, initialValue)

// Callback reducer function
reduceRight(function callbackFn(accumulator, currentValue) { ... })
reduceRight(function callbackFn(accumulator, currentValue, index) { ... })
reduceRight(function callbackFn(accumulator, currentValue, index, array){ ... })
reduceRight(function callbackFn(accumulator, currentValue, index, array) { ... }, initialValue)
```

### ReduceRight parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | Function to execute on each value in the array. |
| initialValue Optional | Value to use as accumulator to the first call of the callbackFn. If no initial value is supplied, the last element in the array will be used and skipped. Calling reduce or reduceRight on an empty array without an initial value creates a TypeError. |

### callbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| accumulator | The value previously returned in the last invocation of the callback, or initialValue, if supplied. |
| currentValue | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. |
| array Optional | The array reduceRight() was called upon. |

## Return value

The value that results from the reduction.


## Exemple
```javascript
const array1 = [[0, 1], [2, 3], [4, 5]].reduceRight(
  (accumulator, currentValue) => accumulator.concat(currentValue)
);

console.log(array1);
// expected output: Array [4, 5, 2, 3, 0, 1]
```