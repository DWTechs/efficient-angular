---
title: From
---

Creates an Observable from an Array, an array-like object, a Promise, an iterable object, or an Observable-like object.


## Syntax

```javascript
from<T>(input: ObservableInput<T>, scheduler?: SchedulerLike): Observable<T>
```

| Parameters | Description |
| ---------- | ----------- |
| input | Type: `ObservableInput`. |
| scheduler Optional | Default is undefined. Type: `SchedulerLike`. |


## Returns

Observable<T>:


## Example

Converts an array to an Observable
```javascript
import { from } from 'rxjs';

const array = [10, 20, 30];
const result = from(array);

result.subscribe(x => console.log(x));

// Logs:
// 10
// 20
// 30
```