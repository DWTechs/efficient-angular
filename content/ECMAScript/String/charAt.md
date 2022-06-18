---
layout: default
title: CharAt
permalink: /javascript/ecmascript/string/charat/

---

Previous : [Table of Contents](./index.md)


# charAt

The String object's charAt() method returns a new string consisting of the single UTF-16 code unit located at the specified offset into the string.


## Syntax

```javascript
charAt(index)
```

### Filter parameters

| Parameters | Description |
| ---------- | ----------- |
| index | An integer between 0 and str.length - 1. If the index cannot be converted to the integer or no index is provided, the default is 0, so the first character of str is returned. |


## Return

An integer between 0 and str.length - 1. If the index cannot be converted to the integer or no index is provided, the default is 0, so the first character of str is returned.


## Example

```javascript
var anyString = 'Brave new world';
console.log("The character at index 0   is '" + anyString.charAt()   + "'"); // The character at index 0   is 'B'
// No index was provided, used 0 as default

console.log("The character at index 0   is '" + anyString.charAt(0)   + "'"); // The character at index 0   is 'B'
console.log("The character at index 1   is '" + anyString.charAt(1)   + "'"); // The character at index 1   is 'r'
console.log("The character at index 2   is '" + anyString.charAt(2)   + "'"); // The character at index 2   is 'a'
console.log("The character at index 3   is '" + anyString.charAt(3)   + "'"); // The character at index 3   is 'v'
console.log("The character at index 4   is '" + anyString.charAt(4)   + "'"); // The character at index 4   is 'e'
console.log("The character at index 999 is '" + anyString.charAt(999) + "'"); // The character at index 999 is ''
```