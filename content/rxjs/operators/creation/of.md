---
title: Of
---

Converts the arguments to an observable sequence.


## Syntax

```javascript
of<T>(...args: (SchedulerLike | T)[]): Observable<T>
```

| Parameters | Description |
| ---------- | ----------- |
| args | Type: `(SchedulerLike | T)[]`. |


## Returns

Observable<T>: An Observable that emits the arguments described above and then completes.


## Example

Emit the values 10, 20, 30
```javascript
import { of } from 'rxjs';
 
of(10, 20, 30)
.subscribe(
  next => console.log('next:', next),
  err => console.log('error:', err),
  () => console.log('the end'),
);
 
// Outputs
// next: 10
// next: 20
// next: 30
// the end
```