---
layout: default
title: Shift
permalink: /javascript/ecmascript/array/shift/

---

Previous : [Table of Contents](./index.md)


# Shift

The shift() method removes the first element from an array and returns that removed element. This method changes the length of the array.


## Syntax

```javascript
shift()
```


## Return value

The removed element from the array; undefined if the array is empty.


## Example

```javascript
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// expected output: Array [2, 3]

console.log(firstElement);
// expected output: 1
```