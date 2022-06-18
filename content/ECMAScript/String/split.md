---
layout: default
title: Split
permalink: /javascript/ecmascript/string/split/

---

Previous : [Table of Contents](./index.md)


# Split

The split() method divides a String into an ordered list of substrings, puts these substrings into an array, and returns the array.  The division is done by searching for a pattern; where the pattern is provided as the first parameter in the method's call.  


## Syntax

```javascript
split()
split(separator)
split(separator, limit)
```

### Split parameters
| Parameters | Description |
| ---------- | ----------- |
| separator Optional | The pattern describing where each split should occur.  The separator can be a simple string or it can be a regular expression. |
| thisArg Optional | A non-negative integer specifying a limit on the number of substrings to be included in the array. If provided, splits the string at each occurrence of the specified separator, but stops when limit entries have been placed in the array. Any leftover text is not included in the array at all. |


## Return

An Array of strings, split at each point where the separator occurs in the given string.


## Example

```javascript
const str = 'The quick brown fox jumps over the lazy dog.';

const words = str.split(' ');
console.log(words[3]);
// expected output: "fox"

const chars = str.split('');
console.log(chars[8]);
// expected output: "k"

const strCopy = str.split();
console.log(strCopy);
// expected output: Array ["The quick brown fox jumps over the lazy dog."]




const myString = ''
const splits = myString.split()

console.log(splits)

// ↪ [""]
```