---
layout: default
title: Repeat
permalink: /javascript/ecmascript/string/repeat/

---

Previous : [Table of Contents](./index.md)


# Repeat

The repeat() method constructs and returns a new string which contains the specified number of copies of the string on which it was called, concatenated together.


## Syntax

```javascript
repeat(count)
```

### Repeat parameters

| Parameters | Description |
| ---------- | ----------- |
| count | An integer between 0 and +Infinity, indicating the number of times to repeat the string. |


## Return

A new string containing the specified number of copies of the given string.


## Example

```javascript
const chorus = 'Because I\'m happy. ';

console.log(`Chorus lyrics for "Happy": ${chorus.repeat(27)}`);

// expected output: "Chorus lyrics for "Happy": Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. "


'abc'.repeat(-1)    // RangeError
'abc'.repeat(0)     // ''
'abc'.repeat(1)     // 'abc'
'abc'.repeat(2)     // 'abcabc'
'abc'.repeat(3.5)   // 'abcabcabc' (count will be converted to integer)
'abc'.repeat(1/0)   // RangeError

({ toString: () => 'abc', repeat: String.prototype.repeat }).repeat(2)
// 'abcabc' (repeat() is a generic method)
```