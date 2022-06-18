---
layout: default
title: Find
permalink: /javascript/ecmascript/array/find/

---

Previous : [Table of Contents](./index.md)


# Find

The find() method returns the value of the first element in an array that pass a test (provided as a function).

The find() method executes the function once for each element present in the array:

If it finds an array element where the function returns a true value, find() returns the value of that array element (and does not check the remaining values)
Otherwise it returns undefined

Note: find() does not execute the function for empty arrays.

Note: find() does not change the original array.


## Syntax
```javascript
array.find(function(currentValue, index, arr),thisValue)
```

### Find parameters
| Parameters | Description |
| ---------- | ----------- |
| function | A function to be run for each element in the array. |

### Function parameters
| Parameters | Description |
| ---------- | ----------- |
| currentValue | The value of the current element. |
| indexOptional | The array index of the current element |
| arr Optional | The array object the current element belongs to |


## Return value
The value of the first element in the array that satisfies the provided testing function. Otherwise, undefined is returned.


## Example
```javascript
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// expected output: 12
```