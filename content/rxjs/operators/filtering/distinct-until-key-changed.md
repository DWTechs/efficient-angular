---
layout: default
title: DistinctUntilKeyChanged
permalink: /javascript/rxjs/operators/filtering/distinctuntilkeychanged/

---

Previous : [Operators](../../operators.md)

# DistinctUntilKeyChanged

Returns an Observable that emits all items emitted by the source Observable that are distinct by comparison from the previous item, using a property accessed by using the key provided to check if the two items are distinct.


## Syntax
```javascript
distinctUntilKeyChanged<T, K extends keyof T>(key: K, compare?: (x: T[K], y: T[K]) => boolean): MonoTypeOperatorFunction<T>
```

| Parameters | Description |
| ---------- | ----------- |
| key | String key for object property lookup on each item. |
| defaultValue Optional | Default is undefined. Comparison function called to test if an item is distinct from the previous item in the source. |

## Returns
MonoTypeOperatorFunction<T>: A function that returns an Observable that emits items from the source Observable with distinct values based on the key specified.

## Example
```javascript
import { of } from 'rxjs';
import { distinctUntilKeyChanged } from 'rxjs/operators';
 
 interface Person {
    age: number,
    name: string
 }
 
of(
    { age: 4, name: 'Foo'},
    { age: 7, name: 'Bar'},
    { age: 5, name: 'Foo'},
    { age: 6, name: 'Foo'},
  ).pipe(
    distinctUntilKeyChanged('name'),
  )
  .subscribe(x => console.log(x));
 
// displays:
// { age: 4, name: 'Foo' }
// { age: 7, name: 'Bar' }
// { age: 5, name: 'Foo' }
```