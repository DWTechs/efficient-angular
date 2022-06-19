---
title: Map
---

Applies a given project function to each value emitted by the source Observable, and emits the resulting values as an Observable.


## Syntax

```javascript
map<T, R>(project: (value: T, index: number) => R, thisArg?: any): OperatorFunction<T, R>
```

| Parameters | Description |
| ---------- | ----------- |
| project | The function to apply to each value emitted by the source Observable. The index parameter is the number i for the i-th emission that has happened since the subscription, starting from the number 0.  |
| thisArg Optional | Default is undefined. An optional argument to define what this is in the project function. |


## Returns
OperatorFunction<T, R>: A function that returns an Observable that emits the values from the source Observable transformed by the given project function.


## Example

Map every click to the clientX position of that click

```javascript
import { fromEvent } from 'rxjs';
import { map } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const positions = clicks.pipe(map(ev => ev.clientX));
positions.subscribe(x => console.log(x));
```