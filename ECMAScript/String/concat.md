---
layout: default
title: Concat
permalink: /javascript/ecmascript/string/concat/

---

Previous : [Table of Contents](./index.md)


# Concat

The concat() method concatenates the string arguments to the calling string and returns a new string.


## Syntax

```javascript
concat(str1)
concat(str1, str2)
concat(str1, str2, ... , strN)
```

### Concat parameters

| Parameters | Description |
| ---------- | ----------- |
| strN | One or more strings to concatenate to str. |


## Return

A new string containing the combined text of the strings provided.


## Example

```javascript
const str1 = 'Hello';
const str2 = 'World';

console.log(str1.concat(' ', str2));
// expected output: "Hello World"

console.log(str2.concat(', ', str1));
// expected output: "World, Hello"
```