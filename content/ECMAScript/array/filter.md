---
layout: default
title: Filter
permalink: /javascript/ecmascript/array/filter/

---

Previous : [Table of Contents](./index.md)


# Filter

The filter() method creates a new array with all elements that pass the test implemented by the provided function.  If no elements pass the test, an empty array will be returned.


## Syntax
```javascript
// Arrow function
filter((element) => { ... } )
filter((element, index) => { ... } )
filter((element, index, array) => { ... } )

// Callback function
filter(callbackFn)
filter(callbackFn, thisArg)

// Inline callback function
filter(function callbackFn(element) { ... })
filter(function callbackFn(element, index) { ... })
filter(function callbackFn(element, index, array){ ... })
filter(function callbackFn(element, index, array) { ... }, thisArg)
```

### Filter parameters
| Parameters | Description |
| ---------- | ----------- |
| callbackFn | Function is a predicate, to test each element of the array. Return a value that coerces to true to keep the element, or to false otherwise. |
| thisArg Optional | engine to be used for processing templates. Handlebars is the default. |



### callbackFn parameters
| Parameters | Description |
| ---------- | ----------- |
| element | The current element being processed in the array. |
| index Optional | The index of the current element being processed in the array. |
| array Optional | The array filter was called upon. |


## Return value
A new array with the elements that pass the test. If no elements pass the test, an empty array will be returned.


## Exemple
```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

