---
title: Debounce
---

Emits a notification from the source Observable only after a particular time span determined by another Observable has passed without another source emission.

## Syntax 

```javascript
debounce<T>(durationSelector: (value: T) => ObservableInput<any>): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| durationSelector | A function that receives a value from the source Observable, for computing the timeout duration for each source value, returned as an Observable or a Promise. |


## Returns

MonoTypeOperatorFunction<T>: A function that returns an Observable that delays the emissions of the source Observable by the specified duration Observable returned by durationSelector, and may drop some values if they occur too frequently.


## Example

Emit the most recent click after a burst of clicks
```javascript
import { fromEvent, interval } from 'rxjs';
import { scan, debounce } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(
  scan((i) => ++i, 1),
  debounce((i) => interval(200 * i))
);
result.subscribe(x => console.log(x));
```