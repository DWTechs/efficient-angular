---
layout: default
title: Substring
permalink: /javascript/ecmascript/string/substring/

---

Previous : [Table of Contents](./index.md)


# Substring

The substring() method returns the part of the string between the start and end indexes, or to the end of the string.


## Syntax

```javascript
substring(indexStart)
substring(indexStart, indexEnd)
```

### Substring parameters
| Parameters | Description |
| ---------- | ----------- |
| indexStart | The index of the first character to include in the returned substring. |
| indexEnd Optional | The index of the first character to exclude from the returned substring. |


## Return

A new string containing the specified part of the given string.


## Example

```javascript
const str = 'Mozilla';

console.log(str.substring(1, 3));
// expected output: "oz"

console.log(str.substring(2));
// expected output: "zilla"



let anyString = 'Mozilla'

// Displays 'M'
console.log(anyString.substring(0, 1))
console.log(anyString.substring(1, 0))

// Displays 'Mozill'
console.log(anyString.substring(0, 6))

// Displays 'lla'
console.log(anyString.substring(4))
console.log(anyString.substring(4, 7))
console.log(anyString.substring(7, 4))

// Displays 'Mozilla'
console.log(anyString.substring(0, 7))
console.log(anyString.substring(0, 10))
```