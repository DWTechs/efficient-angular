---
title: "*ngStyle"
---

The NgStyle directive lets you set a given DOM elements style properties.


## Example

JavaScript
```javascript
let stickerCompareData = false;
let item: any = {
    color: '#000091',
    text: 'text',
    label: 'label'
}
```

HTML
```html
<div (click)="setFullscreen()" [ngStyle]="{'margin-left':fullscreen ? 'auto' : '24px' }"> 
<!-- fullscreen = true -> margin-left: auto ; fullscreen = false -> margin-left: 24px -->

<div class="square" [ngStyle]="{'background-color':item.color}"> </div> 
<!-- background-color: #000091 -->

<div [ngStyle]="stickerCompareData ? {'width': '48%'} : {'width': '100%'}">
<!-- stickerCompareData = true -> 'width': '48% ; fullscreen = false -> width': '100% -->

<div class="sticker-content percentage"  [ngStyle]="{'width': '48%'}">
<!-- width': '48% -->
```