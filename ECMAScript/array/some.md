---
layout: default
title: Some
permalink: /javascript/ecmascript/array/some/

---

Previous : [Table of Contents](./index.md)


# Some

The some() method tests whether at least one element in the array passes the test implemented by the provided function. It returns true if, in the array, it finds an element for which the provided function returns true; otherwise it returns false. It doesn't modify the array.


## Syntax

```javascript
// Arrow function
some((element) => { ... } )
some((element, index) => { ... } )
some((element, index, array) => { ... } )

// Callback function
some(callbackFn)
some(callbackFn, thisArg)

// Inline callback function
some(function callbackFn(element) { ... })
some(function callbackFn(element, index) { ... })
some(function callbackFn(element, index, array){ ... })
some(function callbackFn(element, index, array) { ... }, thisArg)
```

### Some parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | A function to test for each element. |
| thisArg Optional | A value to use as this when executing callbackFn. |



### callbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| element | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. |
| array Optional | The array some() was called upon. |


## Return value

true if the callback function returns a truthy value for at least one element in the array. Otherwise, false.


## Example

```javascript
const array = [1, 2, 3, 4, 5];

// checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// expected output: true
```