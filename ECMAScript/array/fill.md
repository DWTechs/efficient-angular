---
layout: default
title: Fill
permalink: /javascript/ecmascript/array/fill/

---


Previous : [Table of Contents](./index.md)


# Fill

The fill() method changes all elements in an array to a static value, from a start index (default 0) to an end index (default array.length). It returns the modified array.


## Syntax

```javascript
fill(value)
fill(value, start)
fill(value, start, end)
```

### Fill parameters
| Parameters | Description |
| ---------- | ----------- |
| value | Value to fill the array with. (Note all elements in the array will be this exact value.) |
| start Optional | Start index, default 0. |
| end Optional | End index, default arr.length. |


## Return value

The modified array, filled with value.


## Example

```javascript
const array1 = [1, 2, 3, 4];

// fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// expected output: [1, 2, 0, 0]

// fill with 5 from position 1
console.log(array1.fill(5, 1));
// expected output: [1, 5, 5, 5]

console.log(array1.fill(6));
// expected output: [6, 6, 6, 6]
```