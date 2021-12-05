---
layout: default
title: Unshift
permalink: /javascript/ecmascript/array/unshift/

---

Previous : [Table of Contents](./index.md)


# Unshift

The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.


## Syntax

```javascript
unshift(element0)
unshift(element0, element1)
unshift(element0, element1, ... , elementN)
```

### Unshift parameters
| Parameters | Description |
| ---------- | ----------- |
| elementN | The elements to add to the front of the arr. |


## Return value

The new length property of the object upon which the method was called.


## Example

```javascript
const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// expected output: 5

console.log(array1);
// expected output: Array [4, 5, 1, 2, 3]
```