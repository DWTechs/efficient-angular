---
title: Concat
---

Creates an output Observable which sequentially emits all values from the first given Observable and then moves on to the next.


## Syntax 

```javascript
concat(...args: any[]): Observable<unknown>
```

| Parameters | Description |
| ---------- | ----------- |
| otherSources | Other observable sources to subscribe to, in sequence, after the original source is complete. |


## Returns

Observable<unknown>  Observable which sequentially emits all values from the first given Observable and then moves on to the next.


## Example

Concatenate a timer counting from 0 to 3 with a synchronous sequence from 1 to 10

```javascript
import { concat, interval } from 'rxjs';
import { take } from 'rxjs/operators';
 
const timer1 = interval(1000).pipe(take(10));
const timer2 = interval(2000).pipe(take(6));
const timer3 = interval(500).pipe(take(10));
 
const result = concat(timer1, timer2, timer3);
result.subscribe(x => console.log(x));
 
// results in the following:
// (Prints to console sequentially)
// -1000ms-> 0 -1000ms-> 1 -1000ms-> ... 9
// -2000ms-> 0 -2000ms-> 1 -2000ms-> ... 5
// -500ms-> 0 -500ms-> 1 -500ms-> ... 9
```


Concatenate 3 Observables

## Example

```javascript
import { concat, interval } from 'rxjs';
import { take } from 'rxjs/operators';
 
const timer1 = interval(1000).pipe(take(10));
const timer2 = interval(2000).pipe(take(6));
const timer3 = interval(500).pipe(take(10));
 
const result = concat(timer1, timer2, timer3);
result.subscribe(x => console.log(x));
 
// results in the following:
// (Prints to console sequentially)
// -1000ms-> 0 -1000ms-> 1 -1000ms-> ... 9
// -2000ms-> 0 -2000ms-> 1 -2000ms-> ... 5
// -500ms-> 0 -500ms-> 1 -500ms-> ... 9
```


Concatenate the same Observable to repeat it

## Example

```javascript
import { concat, interval } from 'rxjs';
import { take } from 'rxjs/operators';
 
const timer = interval(1000).pipe(take(2));
 
concat(timer, timer) // concatenating the same Observable!
.subscribe(
  value => console.log(value),
  err => {},
  () => console.log('...and it is done!')
);
 
// Logs:
// 0 after 1s
// 1 after 2s
// 0 after 3s
// 1 after 4s
// "...and it is done!" also after 4s
```