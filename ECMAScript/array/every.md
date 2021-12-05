---
layout: default
title: Every
permalink: /javascript/ecmascript/array/every/

---

Previous : [Table of Contents](./index.md)


# Every

The every() method tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value.


## Syntax

```javascript
// Arrow function
every((element) => { ... } )
every((element, index) => { ... } )
every((element, index, array) => { ... } )

// Callback function
every(callbackFn)
every(callbackFn, thisArg)

// Inline callback function
every(function callbackFn(element) { ... })
every(function callbackFn(element, index) { ... })
every(function callbackFn(element, index, array){ ... })
every(function callbackFn(element, index, array) { ... }, thisArg)
```

### Every parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | A function to test for each element |
| thisArg  Optional | A value to use as this when executing callbackFn |

### callbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| element | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. |
| array Optional | The array every was called upon. |


## Return value

true if the callbackFn function returns a truthy value for every array element. Otherwise, false.


## Example

```javascript
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// expected output: true
```