---
layout: default
title: ngIf
permalink: /javascript/angular/directives/ngif/

---


# *ngIf

This directive allows you to hide an element according to the associated expression..<br/>
It removes or adds the element in the DOM.

Note:<br/>
This directive adds or removes the element inside the DOM.<br/>
If you just want to hide it, without removing it, use the CSS :

**display:none** means that the tag in question will not appear on the page at all (although you can still interact with it through the dom).<br/>There will be no space allocated for it between the other tags.

JavaScript
```javascript
let hide = false;
```

HTML
```html
<h2 [ngClass]="'not-displayed' : hide" class="building-text">Show this only if "show"</h2>
<!-- hide = true -> not-displayed -> display: none -->
```

CSS
```CSS
.not-displayed {
    display: none;
}
```

**visibility:hidden** means that unlike display:none, the tag is not visible, but space is allocated for it on the page.<br/> The tag is rendered, it just isn't seen on the page.

JavaScript
```javascript
let hide = false;
```

HTML
```html
<h2 [ngStyle]="{'visibility':hide ? 'hidden' : 'visible' }" class="building-text">Show this only if "show"</h2>
<!-- hide = true -> visibility':'hidden'; hide = false -> visibility':'visible' -->
```

## Example

JavaScript
```javascript
let show = false;
```

HTML
```html
<h2 *ngIf="show" class="building-text">Show this only if "show"</h2>
<!-- show = false -> not displayed, not in the DOM -->
```

in this example, the show variable is false, so the h2 title is not in the DOM.<br/>
If the variable is set to true, the title will be added.<br/>
it will be removed if it is set to false