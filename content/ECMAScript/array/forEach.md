---
layout: default
title: Foreach
permalink: /javascript/ecmascript/array/foreach/

---

Previous : [Table of Contents](./index.md)


# Foreach

The forEach() method executes a provided function once for each array element.

## Syntax
```javascript
// Arrow function
forEach((element) => { ... } )
forEach((element, index) => { ... } )
forEach((element, index, array) => { ... } )

// Callback function
forEach(callbackFn)
forEach(callbackFn, thisArg)

// Inline callback function
forEach(function callbackFn(element) { ... })
forEach(function callbackFn(element, index) { ... })
forEach(function callbackFn(element, index, array){ ... })
forEach(function callbackFn(element, index, array) { ... }, thisArg)
```

### ForEach parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | Function to execute on each element. |
| thisArg Optional | Value to use as this when executing callbackFn. |

### CallbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| element | The current element being processed in the array. |
| index Optional | The index of element in the array. |
| array Optional | The array forEach() was called upon. |


## Return value
undefined.


## Example
```javascript
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// expected output: "a"
// expected output: "b"
// expected output: "c"
```


## Difference between .forEach() and .map()

forEach: This iterates over a list and applies some operation with side effects to each list member (example: saving every list item to the database) and does not return anything.

map: This iterates over a list, transforms each member of that list, and returns another list of the same size with the transformed members (example: transforming list of strings to uppercase). It does not mutate the array on which it is called (although if passed a callback function, it may do so).