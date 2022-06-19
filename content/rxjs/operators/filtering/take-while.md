---
title: TakeWhile
---

Emits values emitted by the source Observable so long as each value satisfies the given predicate, and then completes as soon as this predicate is not satisfied.


## Syntax 

```javascript
takeWhile<T>(predicate: (value: T, index: number) => boolean, inclusive: boolean = false): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| predicate | A function that evaluates a value emitted by the source Observable and returns a boolean. Also takes the (zero-based) index as the second argument. |
| inclusive optional | Default is false. When set to true the value that caused predicate to return false will also be emitted. |


## Returns

MonoTypeOperatorFunction<T>: A function that returns an Observable that emits values from the source Observable so long as each value satisfies the condition defined by the predicate, then completes.


## Example

Emit click events only while the clientX property is greater than 200
```javascript
import { fromEvent } from 'rxjs';
import { takeWhile } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(takeWhile(ev => ev.clientX > 200));
result.subscribe(x => console.log(x));
```