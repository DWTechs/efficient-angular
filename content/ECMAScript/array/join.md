---
layout: default
title: Join
permalink: /javascript/ecmascript/array/join/

---

Previous : [Table of Contents](./index.md)


# Join

The join() method creates and returns a new string by concatenating all of the elements in an array (or an array-like object), separated by commas or a specified separator string. If the array has only one item, then that item will be returned without using the separator.


## Syntax
```javascript
join()
join(separator)
```

### Join parameters
| Parameters | Description |
| ---------- | ----------- |
| separator Optional | Specifies a string to separate each pair of adjacent elements of the array. The separator is converted to a string if necessary. If omitted, the array elements are separated with a comma (","). If separator is an empty string, all elements are joined without any characters in between them. |


## Return value
A string with all array elements joined. If arr.length is 0, the empty string is returned.


## Example
```javascript
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// expected output: "Fire,Air,Water"

console.log(elements.join(''));
// expected output: "FireAirWater"

console.log(elements.join('-'));
// expected output: "Fire-Air-Water"
```