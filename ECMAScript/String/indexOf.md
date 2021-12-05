---
layout: default
title: IndexOf
permalink: /javascript/ecmascript/string/indexof/

---

Previous : [Table of Contents](./index.md)


# IndexOf

The indexOf() method returns the index within the calling String object of the first occurrence of the specified value, starting the search at fromIndex. Returns -1 if the value is not found.


## Syntax

```javascript
indexOf(searchValue)
indexOf(searchValue, fromIndex)
```

### IndexOf parameters

| Parameters | Description |
| ---------- | ----------- |
| searchValue | The string value to search for. If no string is explicitly provided, searchValue will be coerced to "undefined", and this value will be searched for in str. |
| fromIndex  Optional | An integer representing the index at which to start the search. Defaults to 0. For fromIndex values lower than 0, or greater than str.length, the search starts at index 0 and str.length, respectively. |


## Return

The index of the first occurrence of searchValue, or -1 if not found.


## Example

```javascript
'hello world'.indexOf('') // returns 0
'hello world'.indexOf('', 0) // returns 0
'hello world'.indexOf('', 3) // returns 3
'hello world'.indexOf('', 8) // returns 8
```