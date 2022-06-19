---
title: TakeUntil
---

Emits the values emitted by the source Observable until a notifier Observable emits a value.


## Syntax 
```javascript
takeUntil<T>(notifier: ObservableInput<any>): MonoTypeOperatorFunction<T>
```
| Parameters | Description |
| ---------- | ----------- |
| notifier | The Observable whose first emitted value will cause the output Observable of takeUntil to stop emitting values from the source Observable. |


## Returns

MonoTypeOperatorFunction<T>: A function that returns an Observable that emits the values from the source Observable until notifier emits its first value.


## Example

Tick every second until the first click happens
```javascript
import { fromEvent, interval } from 'rxjs';
import { takeUntil } from 'rxjs/operators';

const source = interval(1000);
const clicks = fromEvent(document, 'click');
const result = source.pipe(takeUntil(clicks));
result.subscribe(x => console.log(x));
```