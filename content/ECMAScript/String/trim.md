---
layout: default
title: Trim
permalink: /javascript/ecmascript/string/trim/

---

Previous : [Table of Contents](./index.md)


# Trim

The trim() method removes whitespace from both ends of a string. Whitespace in this context is all the whitespace characters (space, tab, no-break space, etc.) and all the line terminator characters (LF, CR, etc.).


## Syntax

```javascript
trim()
```


## Return

A new string representing str stripped of whitespace from both its beginning and end.

If neither the beginning or end of str has any whitespace, a new string is still returned (essentially a copy of str), with no exception being thrown.

To return a new string with whitespace trimmed from just one end, use trimStart() or trimEnd().


## Example

```javascript
const greeting = '   Hello world!   ';

console.log(greeting);
// expected output: "   Hello world!   ";

console.log(greeting.trim());
// expected output: "Hello world!";
```