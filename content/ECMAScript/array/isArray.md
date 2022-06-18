---
layout: default
title: IsArray
permalink: /javascript/ecmascript/array/isarray/

---

Previous : [Table of Contents](./index.md)


# IsArray

The Array.isArray() method determines whether the passed value is an Array.


## Syntax
```javascript
Array.isArray(value)
```

### FindIndex parameters
| Parameters | Description |
| ---------- | ----------- |
| value | The value to be checked. |


## Return value

true if the value is an Array; otherwise, false.


## Exemple
```javascript
Array.isArray([1, 2, 3]);  // true
Array.isArray({foo: 123}); // false
Array.isArray('foobar');   // false
Array.isArray(undefined);  // false
```