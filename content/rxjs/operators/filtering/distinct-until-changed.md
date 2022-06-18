---
layout: default
title: DistinctUntilChanged
permalink: /javascript/rxjs/operators/filtering/distinctuntilchanged/

---

Previous : [Operators](../../operators.md)

# DistinctUntilChanged

Only emit when the current value is different than the last.

## Syntax 
```javascript
distinctUntilChanged<T, K>(comparator?: (previous: K, current: K) => boolean, keySelector: (value: T) => K = identity as (value: T) => K): MonoTypeOperatorFunction<T>
```

## Returns
MonoTypeOperatorFunction<T>: A function that returns an Observable that emits items from the source Observable with distinct values based on the key specified.

| Parameters | Description |
| ---------- | ----------- |
| comparator Optional | Default is undefined. The operator takes an optional comparison function that will be called to test if an item is distinct from the previous item. The function receives the current and the previous values as parameters and must return a boolean value that determines whether or not that value should be emitted to the observer or be ignored. Since it’s a comparison function, if it returns true, it means that values are the same and hence the value is ignored, otherwise it’s sent to the observer.|
| defaultValue Optional | Default is undefined. Comparison function called to test if an item is distinct from the previous item in the source. |

## Example
```javascript
// RxJS v6+
import { from } from 'rxjs';
import { distinctUntilChanged } from 'rxjs/operators';

// only output distinct values, based on the last emitted value
const source$ = from([
  { name: 'Brian' },
  { name: 'Joe' },
  { name: 'Joe' },
  { name: 'Sue' }
]);

source$
  // custom compare for name
  .pipe(distinctUntilChanged((prev, curr) => prev.name === curr.name))
  // output: { name: 'Brian }, { name: 'Joe' }, { name: 'Sue' }
  .subscribe(console.log);
```