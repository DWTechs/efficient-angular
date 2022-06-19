---
title: Delay
---

Delays the emission of items from the source Observable by a given timeout or until a given Date.


## Syntax

```javascript
delay<T>(due: number | Date, scheduler: SchedulerLike = asyncScheduler): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| due | The delay duration in milliseconds (a number) or a Date until which the emission of the source items is delayed.  |
| scheduler Optional | Default is asyncScheduler. The SchedulerLike to use for managing the timers that handle the time-shift for each item. |


## Returns

MonoTypeOperatorFunction<T>: A function that returns an Observable that delays the emissions of the source Observable by the specified timeout or Date.


## Example

delay each click by one second

```javascript
import { fromEvent } from 'rxjs';
import { delay } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const delayedClicks = clicks.pipe(delay(1000)); // each click emitted after 1 second
delayedClicks.subscribe(x => console.log(x));
```