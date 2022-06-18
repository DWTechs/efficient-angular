---
layout: default
title: TakeLast
permalink: /javascript/rxjs/operators/filtering/takelast/

---

Previous : [Operators](../../operators.md)

# TakeLast

Waits for the source to complete, then emits the last N values from the source, as specified by the count argument.


## Syntax 

```javascript
takeLast<T>(count: number): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| count | The maximum number of values to emit from the end of the sequence of values emitted by the source Observable. |


## Returns

MonoTypeOperatorFunction<T>: A function that returns an Observable that emits at most the last count values emitted by the source Observable.


## Example

Take the last 3 values of an Observable with many values
```javascript
import { range } from 'rxjs';
import { takeLast } from 'rxjs/operators';

const many = range(1, 100);
const lastThree = many.pipe(takeLast(3));
lastThree.subscribe(x => console.log(x));
```