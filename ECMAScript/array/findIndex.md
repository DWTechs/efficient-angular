---
layout: default
title: FindIndex
permalink: /javascript/ecmascript/array/findindex/

---

Previous : [Table of Contents](./index.md)


# FindIndex

The findIndex() method returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test.


## Syntax
```javascript
// Arrow function
findIndex((element) => { ... } )
findIndex((element, index) => { ... } )
findIndex((element, index, array) => { ... } )

// Callback function
findIndex(callbackFn)
findIndex(callbackFn, thisArg)

// Inline callback function
findIndex(function callbackFn(element) { ... })
findIndex(function callbackFn(element, index) { ... })
findIndex(function callbackFn(element, index, array){ ... })
findIndex(function callbackFn(element, index, array) { ... }, thisArg)
```

### FindIndex parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | A function to execute on each value in the array until the function returns true, indicating that the satisfying element was found. |
| thisArg Optional | Object to use as this when executing callbackFn. |

### callbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| element | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. |
| array Optional | The array findIndex() was called upon. |


## Return value

The index of the first element in the array that passes the test. Otherwise, -1.

Note: if the index of the first element in the array that passes the test is 0, the return value of findIndex will be interpreted as Falsy in conditional statements.


## Exemple
```javascript
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// expected output: 3
```