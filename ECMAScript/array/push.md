---
layout: default
title: Push
permalink: /javascript/ecmascript/array/push/

---

Previous : [Table of Contents](./index.md)


# Push

The push() method adds one or more elements to the end of an array and returns the new length of the array.


## Syntax

```javascript
push(element0)
push(element0, element1)
push(element0, element1, ... , elementN)
```

### Push parameters
| Parameters | Description |
| ---------- | ----------- |
| elementN | The element(s) to add to the end of the array. |


## Return value

The new length property of the object upon which the method was called.


## Example

```javascript
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// expected output: 4
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]
```