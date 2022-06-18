---
layout: default
title: StartsWith
permalink: /javascript/ecmascript/string/startwith/

---

Previous : [Table of Contents](./index.md)


# StartsWith

The startsWith() method determines whether a string begins with the characters of a specified string, returning true or false as appropriate.


## Syntax

```javascript
startsWith(searchString)
startsWith(searchString, position)
```

### StartsWith parameters
| Parameters | Description |
| ---------- | ----------- |
| searchString | The characters to be searched for at the start of this string. |
| position Optional | The position in this string at which to begin searching for searchString. Defaults to 0. |


## Return

true if the given characters are found at the beginning of the string; otherwise, false.


## Example

```javascript
const str1 = 'Saturday night plans';

console.log(str1.startsWith('Sat'));
// expected output: true

console.log(str1.startsWith('Sat', 3));
// expected output: false



//startswith
let str = 'To be, or not to be, that is the question.'

console.log(str.startsWith('To be'))          // true
console.log(str.startsWith('not to be'))      // false
console.log(str.startsWith('not to be', 10))  // true
```