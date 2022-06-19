---
title: Tap
---

Used to perform side-effects for notifications from the source observable


## Syntax

```javascript
tap<T>(observerOrNext?: Partial<Observer<T>> | ((value: T) => void), error?: (e: any) => void, complete?: () => void): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| observerOrNext Optional | Optional. Default is undefined. A next handler or partial observer.  |
| error Optional | Default is undefined. An error handler |
| complete Optional | Default is undefined. A completion handler |


## Returns

MonoTypeOperatorFunction<T>: A function that returns an Observable identical to the source, but runs the specified Observer or callback(s) for each item.


## Example

Check a random number before it is handled. Below is an observable that will use a random number between 0 and 1, and emit "big" or "small" depending on the size of that number. But we wanted to log what the original number was, so we have added a tap(console.log).

```javascript
import { of } from 'rxjs';
import { tap, map } from 'rxjs/operators';

of(Math.random()).pipe(
  tap(console.log),
  map(n => n > 0.5 ? 'big' : 'small')
).subscribe(console.log);
```