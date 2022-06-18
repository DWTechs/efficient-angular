---
layout: default
title: Sort
permalink: /javascript/ecmascript/array/sort/

---

Previous : [Table of Contents](./index.md)


# Sort

The sort() method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.


## Syntax
```javascript
// Functionless
sort()

// Arrow function
sort((firstEl, secondEl) => { ... } )

// Compare function
sort(compareFn)

// Inline compare function
sort(function compareFn(firstEl, secondEl) { ... })
```
### Sort parameters
| Parameters | Description |
| ---------- | ----------- |
| compareFunction Optional | Specifies a function that defines the sort order. If omitted, the array elements are converted to strings, then sorted according to each character's Unicode code point value. |

### CompareFunction parameters
| Parameters | Description |
| ---------- | ----------- |
| firstEl | The first element for comparison. |
| secondEl | The second element for comparison. |


## Return value
The sorted array. Note that the array is sorted in place, and no copy is made.


## Example
```javascript
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]
```