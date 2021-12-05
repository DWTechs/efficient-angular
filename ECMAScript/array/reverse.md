---
layout: default
title: Reverse
permalink: /javascript/ecmascript/array/reverse/

---

Previous : [Table of Contents](./index.md)


## Reverse

The reverse() method reverses an array in place. The first array element becomes the last, and the last array element becomes the first.


## Syntax
```javascript
reverse()
```


## Return value
The reversed array.


## Example

```javascript
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);
// expected output: "array1:" Array ["three", "two", "one"]
```