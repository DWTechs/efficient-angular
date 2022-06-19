---
title: DebounceTime
---

Emits a notification from the source Observable only after a particular time span has passed without another source emission.


## Syntax 

```javascript
debounceTime<T>(dueTime: number, scheduler: SchedulerLike = asyncScheduler): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| dueTime | The timeout duration in milliseconds (or the time unit determined internally by the optional scheduler) for the window of time required to wait for emission silence before emitting the most recent source value. |
| scheduler optional | Default is asyncScheduler. The SchedulerLike to use for managing the timers that handle the timeout for each value. |


## Returns

MonoTypeOperatorFunction<T>: A function that returns an Observable that delays the emissions of the source Observable by the specified dueTime, and may drop some values if they occur too frequently.


## Example

Emit the most recent click after a burst of clicks
```javascript
import { fromEvent } from 'rxjs';
import { debounceTime } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(debounceTime(1000));
result.subscribe(x => console.log(x));
```