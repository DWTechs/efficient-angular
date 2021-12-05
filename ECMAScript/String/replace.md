---
layout: default
title: Replace
permalink: /javascript/ecmascript/string/replace/

---

Previous : [Table of Contents](./index.md)


# Replace

The replace() method returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match. If pattern is a string, only the first occurrence will be replaced.
The original string is left unchanged.


## Syntax

```javascript
replace(regexp, newSubstr)
replace(regexp, replacerFunction)

replace(substr, newSubstr)
replace(substr, replacerFunction)
```

### Replace parameters

| Parameters | Description |
| ---------- | ----------- |
| regexp (pattern) | A RegExp object or literal. The match or matches are replaced with newSubstr or the value returned by the specified replacerFunction. |
| substr | A String that is to be replaced by newSubstr. It is treated as a literal string and is not interpreted as a regular expression. Only the first occurrence will be replaced. |
| newSubstr (replacement) | The String that replaces the substring specified by the specified regexp or substr parameter. A number of special replacement patterns are supported; see the "Specifying a string as a parameter" section below. If newSubstr is an empty string, then the substring given by substr, or the matches for regexp, are removed (rather then being replaced). |
| replacerFunction (replacement) | A function to be invoked to create the new substring to be used to replace the matches to the given regexp or substr. The arguments supplied to this function are described in the "Specifying a function as a parameter" section below. |


## Return

A new string, with some or all matches of a pattern replaced by a replacement.


## Example

```javascript
const p = 'The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?';

console.log(p.replace('dog', 'monkey'));
// expected output: "The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?"


const regex = /Dog/i;
console.log(p.replace(regex, 'ferret'));
// expected output: "The quick brown fox jumps over the lazy ferret. If the dog reacted, was it really lazy?"

```