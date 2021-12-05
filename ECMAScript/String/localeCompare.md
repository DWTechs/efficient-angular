---
layout: default
title: LocaleCompare
permalink: /javascript/ecmascript/string/localecompare/

---

Previous : [Table of Contents](./index.md)


# LocaleCompare

The localeCompare() method returns a number indicating whether a reference string comes before, or after, or is the same as the given string in sort order.


## Syntax

```javascript
localeCompare(compareString)
localeCompare(compareString, locales)
localeCompare(compareString, locales, options)
```

### LocaleCompare parameters
| Parameters | Description |
| ---------- | ----------- |
| locales and options | Function is a predicate, to test each element of the array. Return a value that coerces to true to keep the element, or to false otherwise. |
| thisArg Optional | These arguments customize the behavior of the function and let applications specify the language whose formatting conventions should be used. In implementations which ignore the locales and options arguments, the locale used and the form of the string returned are entirely implementation-dependent. [more details](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Collator/Collator) |


## Return

A negative number if referenceStr occurs before compareString; positive if the referenceStr occurs after compareString; 0 if they are equivalent.


## Example

```javascript
const a = 'réservé'; // with accents, lowercase
const b = 'RESERVE'; // no accents, uppercase

console.log(a.localeCompare(b));
// expected output: 1
console.log(a.localeCompare(b, 'en', { sensitivity: 'base' }));
// expected output: 0


// The letter "a" is before "c" yielding a negative value
'a'.localeCompare('c'); // -2 or -1 (or some other negative value)

// Alphabetically the word "check" comes after "against" yielding a positive value
'check'.localeCompare('against'); // 2 or 1 (or some other positive value)

// "a" and "a" are equivalent yielding a neutral value of zero
'a'.localeCompare('a'); // 0
```