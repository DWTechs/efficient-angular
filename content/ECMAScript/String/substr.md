---
layout: default
title: Substr
permalink: /javascript/ecmascript/string/substr/

---

Previous : [Table of Contents](./index.md)


# Substr

The substr() method returns a portion of the string, starting at the specified index and extending for a given number of characters afterwards.


## Syntax

```javascript
substr(start)
substr(start, length)
```

### Substr parameters
| Parameters | Description |
| ---------- | ----------- |
| start | The index of the first character to include in the returned substring. |
| length Optional | The number of characters to extract. |


## Return

A new string containing the specified part of the given string.


## Example

```javascript
const str = 'Mozilla';

console.log(str.substr(1, 2));
// expected output: "oz"

console.log(str.substr(2));
// expected output: "zilla"

```