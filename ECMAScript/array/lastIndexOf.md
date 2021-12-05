---
layout: default
title: LastIndexOf
permalink: /javascript/ecmascript/array/lastindexof/

---

Previous : [Table of Contents](./index.md)


# LastIndexOf

The lastIndexOf() method returns the index within the calling String object of the last occurrence of the specified value, searching backwards from fromIndex. Returns -1 if the value is not found.


## Syntax
```javascript
lastIndexOf(searchValue)
lastIndexOf(searchValue, fromIndex)
```

### LastIndexOf parameters
| Parameters | Description |
| ---------- | ----------- |
| searchValue | A string representing the value to search for. If searchValue is an empty string, then fromIndex is returned. |
| fromIndex Optional | The index of the last character in the string to be considered as the beginning of a match. The default value is +Infinity. If fromIndex >= str.length, the whole string is searched. If fromIndex < 0, the behavior will be the same as if it would be 0. |


## Return value

The index of the last occurrence of searchValue; -1 if not found.


## Exemple
```javascript
const paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

const searchTerm = 'dog';

console.log(`The index of the first "${searchTerm}" from the end is ${paragraph.lastIndexOf(searchTerm)}`);
// expected output: "The index of the first "dog" from the end is 52"
```