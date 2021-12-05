---
layout: default
title: Concat
permalink: /javascript/ecmascript/array/concat/

---

Previous : [Table of Contents](./index.md)


# Concat

The concat() method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.


## Syntax

```javascript
concat()
concat(value0)
concat(value0, value1)
concat(value0, value1, ... , valueN)
```
### Concat parameters
| Parameters | Description |
| ---------- | ----------- |
| valueN Optional | Arrays and/or values to concatenate into a new array. If all valueN parameters are omitted, concat returns a shallow copy of the existing array on which it is called. See the description below for more details. |


## Return value

A new Array instance.


## Example

```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```