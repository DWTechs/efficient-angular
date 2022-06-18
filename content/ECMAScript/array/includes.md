---
layout: default
title: Includes
permalink: /javascript/ecmascript/array/includes/

---

Previous : [Table of Contents](./index.md)


# Includes

The includes() method determines whether an array includes a certain value among its entries, returning true or false as appropriate.


## Syntax

```javascript
includes(searchElement)
includes(searchElement, fromIndex)
```

### Includes parameters
| Parameters | Description |
| ---------- | ----------- |
| searchElement | The value to search for. When comparing strings and characters, includes() is case-sensitive. |
| fromIndex Optional | The position in this array at which to begin searching for searchElement. The first element to be searched is found at fromIndex for positive values of fromIndex, or at arr.length + fromIndex for negative values of fromIndex (using the absolute value of fromIndex as the number of elements from the end of the array at which to start the search). Defaults to 0. |


## Return value

A Boolean which is true if the value searchElement is found within the array (or the part of the array indicated by the index fromIndex, if specified).

Values of zero are all considered to be equal, regardless of sign. (That is, -0 is considered to be equal to both 0 and +0), but false is not considered to be the same as 0.


## Example

```javascript
[1, 2, 3].includes(2)         // true
[1, 2, 3].includes(4)         // false
[1, 2, 3].includes(3, 3)      // false
[1, 2, 3].includes(3, -1)     // true
[1, 2, NaN].includes(NaN)     // true
["1", "2", "3"].includes(3)   // false
```