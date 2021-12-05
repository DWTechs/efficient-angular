---
layout: default
title: ToLocaleUpperCase
permalink: /javascript/ecmascript/string/tolocaleuppercase/

---

Previous : [Table of Contents](./index.md)


# ToLocaleUpperCase

The toLocaleUpperCase() method returns the calling string value converted to upper case, according to any locale-specific case mappings.


## Syntax

```javascript
toLocaleUpperCase()
toLocaleUpperCase(locale)
toLocaleUpperCase([locale1, locale2, ...])
```

### ToLocaleUpperCase parameters

| Parameters | Description |
| ---------- | ----------- |
| locale Optional | The locale parameter indicates the locale to be used to convert to upper case according to any locale-specific case mappings. If multiple locales are given in an Array, the best available locale is used. The default locale is the host environment’s current locale. |
| thisArg Optional | engine to be used for processing templates. Handlebars is the default. |


## Return

A new string representing the calling string converted to upper case, according to any locale-specific case mappings.


## Example

```javascript
const city = 'istanbul';

console.log(city.toLocaleUpperCase('en-US'));
// expected output: "ISTANBUL"

console.log(city.toLocaleUpperCase('TR'));
// expected output: "İSTANBUL"


'alphabet'.toLocaleUpperCase(); // 'ALPHABET'

'Gesäß'.toLocaleUpperCase(); // 'GESÄSS'

'i\u0307'.toLocaleUpperCase('lt-LT'); // 'I'

let locales = ['lt', 'LT', 'lt-LT', 'lt-u-co-phonebk', 'lt-x-lietuva'];
'i\u0307'.toLocaleUpperCase(locales); // 'I'
```