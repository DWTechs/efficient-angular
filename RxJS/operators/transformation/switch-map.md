---
layout: default
title: SwitchMap
permalink: /javascript/rxjs/operators/transformation/switchmap/

---

Previous : [Operators](../../operators.md)

# SwitchMap

Projects each source value to an Observable which is merged in the output Observable, emitting values only from the most recently projected Observable.


## Syntax

```javascript
switchMap<T, R, O extends ObservableInput<any>>(project: (value: T, index: number) => O, resultSelector?: (outerValue: T, innerValue: ObservedValueOf<O>, outerIndex: number, innerIndex: number) => R): OperatorFunction<T, ObservedValueOf<O> | R>
```

| Parameters | Description |
| ---------- | ----------- |
| project | A function that, when applied to an item emitted by the source Observable, returns an Observable. |
| resultSelector optional | Optional. Default is undefined. Type: (outerValue: T, innerValue: ObservedValueOf, outerIndex: number, innerIndex: number) => R. |


## Returns

OperatorFunction<T, ObservedValueOf<O> | R>: A function that returns an Observable that emits the result of applying the projection function (and the optional deprecated resultSelector) to each item emitted by the source Observable and taking only the values from the most recently projected inner Observable.


## Example : 

Generate new Observable according to source Observable values

```javascript
import { of } from 'rxjs';
import { switchMap } from 'rxjs/operators';

const switched = of(1, 2, 3).pipe(switchMap((x: number) => of(x, x ** 2, x ** 3)));
switched.subscribe(x => console.log(x));
// outputs
// 1
// 1
// 1
// 2
// 4
// 8
// ... and so on
```