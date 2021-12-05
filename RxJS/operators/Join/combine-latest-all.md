---
layout: default
title: combineLatestAll
permalink: /javascript/rxjs/operators/join/combinelatestall/

---

Previous : [Operators](../../operators.md)

# combineLatestAll

Flattens an Observable-of-Observables by applying combineLatest when the Observable-of-Observables completes.


## Syntax 

```javascript
combineLatestAll<R>(project?: (...values: any[]) => R)
```

| Parameters | Description |
| ---------- | ----------- |
| project Optional | Default is undefined. Function to map the most recent values from each inner Observable into a new result. Takes each of the most recent values from each collected inner Observable as arguments, in order. |


## Example

Map two click events to a finite interval Observable, then apply combineLatestAll

```javascript
import { fromEvent, interval } from 'rxjs';
import { map, combineLatestAll, take } from 'rxjs/operators';
 
const clicks = fromEvent(document, 'click');
const higherOrder = clicks.pipe(
  map(ev =>
     interval(Math.random() * 2000).pipe(take(3))
  ),
  take(2)
);
const result = higherOrder.pipe(
  combineLatestAll()
);
 
result.subscribe(x => console.log(x));
```
