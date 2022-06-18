---
layout: default
title: Flat
permalink: /javascript/ecmascript/array/flat/

---

Previous : [Table of Contents](./index.md)


# Flat

The flat() method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.


## Syntax

```javascript
flat()
flat(depth)
```

### Flat parameters
| Parameters | Description |
| ---------- | ----------- |
| depth Optional | The depth level specifying how deep a nested array structure should be flattened. Defaults to 1. |


## Return value

A new array with the sub-array elements concatenated into it.


## Example

```javascript
const arr1 = [0, 1, 2, [3, 4]];

console.log(arr1.flat());
// expected output: [0, 1, 2, 3, 4]

const arr2 = [0, 1, 2, [[[3, 4]]]];

console.log(arr2.flat(2));
// expected output: [0, 1, 2, [3, 4]]
```