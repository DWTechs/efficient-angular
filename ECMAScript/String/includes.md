---
layout: default
title: Includes
permalink: /javascript/ecmascript/string/includes/

---

Previous : [Table of Contents](./index.md)


# Includes

The includes() method performs a case-sensitive search to determine whether one string may be found within another string, returning true or false as appropriate.


## Syntax

```javascript
includes(searchString)
includes(searchString, position)
```

### Includes parameters
| Parameters | Description |
| ---------- | ----------- |
| searchString | A string to be searched for within str. |
| position  Optional | The position within the string at which to begin searching for searchString. (Defaults to 0.) |


## Return

true if the search string is found anywhere within the given string; otherwise, false if not.


## Example

```javascript
const sentence = 'The quick brown fox jumps over the lazy dog.';

const word = 'fox';

console.log(`The word "${word}" ${sentence.includes(word) ? 'is' : 'is not'} in the sentence`);
// expected output: "The word "fox" is in the sentence"
```