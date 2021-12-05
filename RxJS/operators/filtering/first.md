---
layout: default
title: First
permalink: /javascript/rxjs/operators/filtering/first/

---

Previous : [Operators](../../operators.md)

# First

Emits only the first value (or the first value that meets some condition) emitted by the source Observable.

## Syntax 

```javascript
first<T, D>(predicate?: (value: T, index: number, source: Observable<T>) => boolean, defaultValue?: D): OperatorFunction<T, T | D>
```

| Parameters | Description |
| ---------- | ----------- |
| predicate Optional | condition to match  |
| defaultValue Optional | value to emit if no value matches the condition |

1. Emits the first value if no predicate is present
2. Emits the first matching value if the predicate is present
3. Closes the stream after emitting a value
4. If the source completes before emitting any matching value, then it raises the error notification.


## Returns

OperatorFunction<T, T | D>: A function that returns an Observable that emits the first item that matches the condition.


## Example

```javascript
import { fromEvent } from 'rxjs';
import { first } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(first(ev => ev.target.tagName === 'DIV'));
result.subscribe(x => console.log(x));
```