---
layout: default
title: From
permalink: /javascript/ecmascript/array/from/

---

Previous : [Table of Contents](./index.md)


# From

The Array.from() static method creates a new, shallow-copied Array instance from an array-like or iterable object.


## Syntax
```javascript
// Arrow function
Array.from(arrayLike, (element) => { ... } )
Array.from(arrayLike, (element, index) => { ... } )
Array.from(arrayLike, (element, index, array) => { ... } )

// Mapping function
Array.from(arrayLike, mapFn)
Array.from(arrayLike, mapFn, thisArg)

// Inline mapping function
Array.from(arrayLike, function mapFn(element) { ... })
Array.from(arrayLike, function mapFn(element, index) { ... })
Array.from(arrayLike, function mapFn(element, index, array){ ... })
Array.from(arrayLike, function mapFn(element, index, array) { ... }, thisArg)

```

### From parameters
| Parameters | Description |
| ---------- | ----------- |
| arrayLike | An array-like or iterable object to convert to an array. |
| mapFn Optional | Map function to call on every element of the array. |
| thisArg Optional | Value to use as this when executing mapFn. |

## Return value

A new Array instance.


## Exemple
```javascript
console.log(Array.from('foo'));
// expected output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], x => x + x));
// expected output: Array [2, 4, 6]
```