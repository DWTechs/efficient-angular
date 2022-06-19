---
title: ConcatWith
---

Emits all of the values from the source observable, then, once it completes, subscribes to each observable source provided, one at a time, emitting all of their values, and not subscribing to the next one until it completes.


## Syntax 

```javascript
concatWith<T, A extends readonly unknown[]>(...otherSources: any[]): OperatorFunction<T, T | A[number]>
```

| Parameters | Description |
| ---------- | ----------- |
| otherSources | Other observable sources to subscribe to, in sequence, after the original source is complete. |


## Returns

A function that returns an Observable that concatenates subscriptions to the source and provided Observables subscribing to the next only once the current subscription completes.


## Example

Listen for one mouse click, then listen for all mouse moves.

```javascript
import { fromEvent } from 'rxjs';
import { concatWith } from 'rxjs/operators';
 
const clicks$ = fromEvent(document, 'click');
const moves$ = fromEvent(document, 'mousemove');
 
clicks$.pipe(
  map(() => 'click'),
  take(1),
  concatWith(
    moves$.pipe(
      map(() => 'move')
    )
  )
)
.subscribe(x => console.log(x));
 
// 'click'
// 'move'
// 'move'
// 'move'
// ...
```