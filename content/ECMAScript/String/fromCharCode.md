---
layout: default
title: FromCharCode
permalink: /javascript/ecmascript/string/fromcharcode/

---

Previous : [Table of Contents](./index.md)


# FromCharCode

The static String.fromCharCode() method returns a string created from the specified sequence of UTF-16 code units.


## Syntax

```javascript
String.fromCharCode(num1)
String.fromCharCode(num1, num2)
String.fromCharCode(num1, num2, ..., numN)
```

### FromCharCode parameters

| Parameters | Description |
| ---------- | ----------- |
| num1, ..., numN | A sequence of numbers that are UTF-16 code units. The range is between 0 and 65535 (0xFFFF). Numbers greater than 0xFFFF are truncated. No validity checks are performed. |


## Return

A string of length N consisting of the N specified UTF-16 code units.


## Example

```javascript
String.fromCharCode(65, 66, 67);   // returns "ABC"
String.fromCharCode(0x2014);       // returns "—"
String.fromCharCode(0x12014);      // also returns "—"; the digit 1 is truncated and ignored
String.fromCharCode(8212);         // also returns "—"; 8212 is the decimal form of 0x2014
```