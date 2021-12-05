---
layout: default
title: Search
permalink: /javascript/ecmascript/string/search/

---

Previous : [Table of Contents](./index.md)


# Search

The search() method executes a search for a match between a regular expression and this String object.


## Syntax

```javascript
search(regexp)
```

### Search parameters

| Parameters | Description |
| ---------- | ----------- |
| regexp | A regular expression object. If a non-RegExp object regexp is passed, it is implicitly converted to a RegExp with new RegExp(regexp). |


## Return


## Example

```javascript
const paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

// any character that is not a word character or whitespace
const regex = /[^\w\s]/g;

console.log(paragraph.search(regex));
// expected output: 43

console.log(paragraph[paragraph.search(regex)]);
// expected output: "."



let str = "hey JudE"
let re = /[A-Z]/g
let reDot = /[.]/g
console.log(str.search(re))    // returns 4, which is the index of the first capital letter "J"
console.log(str.search(reDot)) // returns -1 cannot find '.' dot punctuation
```