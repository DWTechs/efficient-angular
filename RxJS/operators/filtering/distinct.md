---
layout: default
title: Distinct
permalink: /javascript/rxjs/operators/filtering/distinct/

---

Previous : [Operators](../../operators.md)


# Distinct

Returns an Observable that emits all items emitted by the source Observable that are distinct by comparison from previous items.

## Syntax
```javascript
distinct(keySelector?, flushes?): Observable
```

| Parameters | Description |
| ---------- | ----------- |
| keySelector Optional | Default is undefined. Function to select which value you want to check as distinct.  |
| flushes Optional | Default is undefined. Observable for flushing the internal HashSet of the operator. |

## Returns
MonoTypeOperatorFunction<T>: A function that returns an Observable that emits items from the source Observable with distinct values.

## Example
```javascript
import { of } from 'rxjs';
import { distinct } from 'rxjs/operators';
 
interface Person {
   age: number,
   name: string
}
 
of(
    { age: 4, name: 'Foo'},
    { age: 7, name: 'Bar'},
    { age: 5, name: 'Foo'}
  ).pipe(
    distinct((p: Person) => p.name)
  )
  .subscribe(x => console.log(x));
 
// Outputs
// { age: 4, name: 'Foo' }
// { age: 7, name: 'Bar' }
```