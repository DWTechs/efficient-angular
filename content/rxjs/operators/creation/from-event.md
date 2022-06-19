---
title: FromEvent
---

Creates an Observable that emits events of a specific type coming from the given event target.


## Syntax

```javascript
fromEvent<T>(target: any, eventName: string, options?: EventListenerOptions | ((...args: any[]) => T), 
resultSelector?: (...args: any[]) => T): Observable<T>
```

| Parameters | Description |
| ---------- | ----------- |
| target | The DOM EventTarget, Node.js EventEmitter, JQuery-like event target, NodeList or HTMLCollection to attach the event handler to. |
| eventName | The event name of interest, being emitted by the target. |
| options optional | Default is undefined. Options to pass through to addEventListener |
| resultSelector optional | Default is undefined. Type: `(...args: any[]) => T.` |


## Returns

```javascript
Observable<T>: 
```
An observable that emits events of a specific type coming from the given event target.


## Examples

Emits clicks happening on the DOM document
```javascript
import { fromEvent } from 'rxjs';

const clicks = fromEvent(document, 'click');
clicks.subscribe(x => console.log(x));

// Results in:
// MouseEvent object logged to console every time a click
// occurs on the document.
```

Use addEventListener with capture option
```javascript
import { fromEvent } from 'rxjs';
 
const clicksInDocument = fromEvent(document, 'click', true); // note optional configuration parameter
                                                             // which will be passed to addEventListener
const clicksInDiv = fromEvent(someDivInDocument, 'click');
 
clicksInDocument.subscribe(() => console.log('document'));
clicksInDiv.subscribe(() => console.log('div'));
 
// By default events bubble UP in DOM tree, so normally
// when we would click on div in document
// "div" would be logged first and then "document".
// Since we specified optional `capture` option, document
// will catch event when it goes DOWN DOM tree, so console
// will log "document" and then "div".
```