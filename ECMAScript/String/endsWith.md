---
layout: default
title: EndsWith
permalink: /javascript/ecmascript/string/endswith/

---

Previous : [Table of Contents](./index.md)


# EndsWith

The endsWith() method determines whether a string ends with the characters of a specified string, returning true or false as appropriate.


## Syntax

```javascript
endsWith(searchString)
endsWith(searchString, length)
```

### EndsWith parameters

| Parameters | Description |
| ---------- | ----------- |
| searchString | The characters to be searched for at the end of str. |
| length Optional | If provided, it is used as the length of str. Defaults to str.length. |


## Return

true if the given characters are found at the end of the string; otherwise, false.


## Example

```javascript
const str1 = 'Cats are the best!';

console.log(str1.endsWith('best', 17));
// expected output: true

const str2 = 'Is this a question';

console.log(str2.endsWith('?'));
// expected output: false
```