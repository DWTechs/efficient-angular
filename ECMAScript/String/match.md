---
layout: default
title: Match
permalink: /javascript/ecmascript/string/match/

---

Previous : [Table of Contents](./index.md)


# Match

The match() method retrieves the result of matching a string against a regular expression.


## Syntax

```javascript
match(regexp)
```

### Match parameters
| Parameters | Description |
| ---------- | ----------- |
| regexp | A regular expression object. If regexp is a non-RegExp object, it is implicitly converted to a RegExp by using new RegExp(regexp). If you don't give any parameter and use the match() method directly, you will get an Array with an empty string: [""]. |


## Return

An Array whose contents depend on the presence or absence of the global (g) flag, or null if no matches are found.

- If the g flag is used, all results matching the complete regular expression will be returned, but capturing groups will not.
- if the g flag is not used, only the first complete match and its related capturing groups are returned. In this case, the returned item will have additional properties as described below.


## Example

```javascript
const paragraph = 'The quick brown fox jumps over the lazy dog. It barked.';
const regex = /[A-Z]/g;
const found = paragraph.match(regex);

console.log(found);
// expected output: Array ["T", "I"]

```