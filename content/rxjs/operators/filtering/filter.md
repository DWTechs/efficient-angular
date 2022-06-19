---
title: Filter
---

Filter items emitted by the source Observable by only emitting those that satisfy a specified predicate.


## Syntax
```javascript
filter<T>(predicate: (value: T, index: number) => boolean, thisArg?: any): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| predicate | A function that evaluates each value emitted by the source Observable. If it returns true, the value is emitted, if false the value is not passed to the output Observable. The index parameter is the number i for the i-th source emission that has happened since the subscription, starting from the number 0.  |
| thisArg Optional | Default is undefined. An optional argument to determine the value of this in the predicate function. |


## Returns
MonoTypeOperatorFunction<T>: A function that returns an Observable that emits items from the source Observable that satisfy the specified predicate.


## Example

Emit only click events whose target was a DIV element
```javascript
import { fromEvent } from 'rxjs';
import { filter } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const clicksOnDivs = clicks.pipe(filter(ev => ev.target.tagName === 'DIV'));
clicksOnDivs.subscribe(x => console.log(x));
```