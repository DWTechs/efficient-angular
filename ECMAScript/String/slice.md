---
layout: default
title: Slice
permalink: /javascript/ecmascript/string/slice/

---

Previous : [Table of Contents](./index.md)


# Slice

The slice() method extracts a section of a string and returns it as a new string, without modifying the original string.


## Syntax

```javascript
slice(beginIndex)
slice(beginIndex, endIndex)
```

### Slice parameters

| Parameters | Description |
| ---------- | ----------- |
| beginIndex | The zero-based index at which to begin extraction. If negative, it is treated as str.length + beginIndex. (For example, if beginIndex is -3, it is treated as str.length - 3.) If beginIndex is not a number after Number(beginIndex), it is treated as 0. If beginIndex is greater than or equal to str.length, an empty string is returned. |
| endIndex  Optional | The zero-based index before which to end extraction. The character at this index will not be included. If endIndex is omitted or undefined, slice() extracts to the end of the string. If endIndex is greater than str.length, slice() also extracts to the end of the string. If endIndex is negative, slice() is treated as str.length + endIndex. If endIndex represents a position that is before the one represented by startIndex, slice() returns "". |


## Return

A new string containing the extracted section of the string.


## Example

```javascript
const str = 'The quick brown fox jumps over the lazy dog.';

console.log(str.slice(31));
// expected output: "the lazy dog."

console.log(str.slice(4, 19));
// expected output: "quick brown fox"

console.log(str.slice(-4));
// expected output: "dog."

console.log(str.slice(-9, -5));
// expected output: "lazy"




let str1 = 'The morning is upon us.', // the length of str1 is 23.
    str2 = str1.slice(1, 8),
    str3 = str1.slice(4, -2),
    str4 = str1.slice(12),
    str5 = str1.slice(30);
console.log(str2)  // OUTPUT: he morn
console.log(str3)  // OUTPUT: morning is upon u
console.log(str4)  // OUTPUT: is upon us.
console.log(str5)  // OUTPUT: ""
```