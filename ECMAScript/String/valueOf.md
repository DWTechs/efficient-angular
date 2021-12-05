---
layout: default
title: ValueOf
permalink: /javascript/ecmascript/string/valueof/

---

Previous : [Table of Contents](./index.md)


# ValueOf

The valueOf() method returns the primitive value of the specified object.


## Syntax

```javascript
valueOf()
```


## Return

The primitive value of the specified object.


## Example

```javascript
function MyNumberType(n) {
  this.number = n;
}

MyNumberType.prototype.valueOf = function() {
  return this.number;
};

const object1 = new MyNumberType(4);

console.log(object1 + 3);
// expected output: 7
```