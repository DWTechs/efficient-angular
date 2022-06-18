---
layout: default
title: Pop
permalink: /javascript/ecmascript/array/pop/

---

Previous : [Table of Contents](./index.md)


# Pop

The pop() method removes the last element from an array and returns that element. This method changes the length of the array.


## Syntax

```javascript
pop()
```


## Return value

The removed element from the array; undefined if the array is empty.


## Example

```javascript
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// expected output: "tomato"

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop();

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage"]
```