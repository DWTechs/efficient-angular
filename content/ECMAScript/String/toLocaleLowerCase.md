---
layout: default
title: ToLocaleLowerCase
permalink: /javascript/ecmascript/string/tolocalelowercase/

---

Previous : [Table of Contents](./index.md)


# ToLocaleLowerCase

The toLocaleLowerCase() method returns the calling string value converted to lower case, according to any locale-specific case mappings.


## Syntax

```javascript
toLocaleLowerCase()
toLocaleLowerCase(locale)
toLocaleLowerCase([locale1, locale2, ...])
```

### ToLocaleLowerCase parameters

| Parameters | Description |
| ---------- | ----------- |
| locale Optional |The locale parameter indicates the locale to be used to convert to lower case according to any locale-specific case mappings. If multiple locales are given in an Array, the best available locale is used. The default locale is the host environment’s current locale. |


## Return

A new string representing the calling string converted to lower case, according to any locale-specific case mappings.


## Example

```javascript
const dotted = 'İstanbul';

console.log(`EN-US: ${dotted.toLocaleLowerCase('en-US')}`);
// expected output: "i̇stanbul"

console.log(`TR: ${dotted.toLocaleLowerCase('tr')}`);
// expected output: "istanbul"


'ALPHABET'.toLocaleLowerCase(); // 'alphabet'

'\u0130'.toLocaleLowerCase('tr') === 'i';    // true
'\u0130'.toLocaleLowerCase('en-US') === 'i'; // false

let locales = ['tr', 'TR', 'tr-TR', 'tr-u-co-search', 'tr-x-turkish'];
'\u0130'.toLocaleLowerCase(locales) === 'i'; // true
```