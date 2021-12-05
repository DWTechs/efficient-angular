---
layout: default
title: ngClass
permalink: /javascript/angular/directives/ngclass/

---


# ngClass


Allows you to add and remove CSS classes on an HTML element.


## Example

JavaScript
```javascript
let isValid = false;
let step = 'step2';
let index = 1;
```

HTML
```html
<div [ngClass]="{'my_class1': step === 'step1', 'my_class2 my_class3' : step === 'step2' }"></div> 
<!-- step === 'step1' -> my_class1 ; step === 'step2' -> my_class2 my_class3 -->

<div [ngClass]="{1 : 'my_class1', 2 : 'my_class2', 3 : 'my_class3'}[index]"></div>
<!-- index === 1 -> my_class1 ; index === 2 -> my_class2 index === 3 -> my_class3 -->

<div [ngClass]="isValid ? 'my_class1' : 'my_class2'"></div>
<!-- isValid = true -> my_class1 ; isValid = false -> my_class2  -->
```