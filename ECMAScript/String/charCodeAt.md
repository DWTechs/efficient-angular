---
layout: default
title: CharCodeAt
permalink: /javascript/ecmascript/string/charcodeat/

---

Previous : [Table of Contents](./index.md)


# CharCodeAt

The charCodeAt() method returns an integer between 0 and 65535 representing the UTF-16 code unit at the given index.


## Syntax

```javascript
charCodeAt(index)
```

### CharCodeAt parameters

| Parameters | Description |
| ---------- | ----------- |
| index | An integer greater than or equal to 0 and less than the length of the string. If index is not a number, it defaults to 0. |


## Return

A number representing the UTF-16 code unit value of the character at the given index. If index is out of range, charCodeAt() returns NaN.


## Example

```javascript
const sentence = 'The quick brown fox jumps over the lazy dog.';

const index = 4;

console.log(`The character code ${sentence.charCodeAt(index)} is equal to ${sentence.charAt(index)}`);
// expected output: "The character code 113 is equal to q"
```