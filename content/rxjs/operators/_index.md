---
layout: default
title: Operators
permalink: /javascript/rxjs/operator/

---

Allow complex asynchronous code to be easily composed in a declarative manner (functional programming).

RxJS provides natively more than a hundred operators.

An operator allows to define an Observable from another one by applying some transformations.

Example

```javascript
import { of } from 'rxjs';
import { filter, map } from 'rxjs/operators';

const squareOdd = of(1, 2, 3, 4, 5)
  .pipe(
    filter(n => n % 2 !== 0), // odd values only
    map(n => n * n) //Square odd values
  );

// Subscribe to get values
squareOdd.subscribe(x => console.log(x));
```

## Pipe

Pipeable Operators are the kind that can be piped to Observables. When called, they do not change the existing Observable instance. Instead, they return a new Observable, whose subscription logic is based on the first Observable.

A Pipeable Operator is a function that takes an Observable as its input and returns another Observable. It is a pure operation: the previous Observable stays unmodified.

A Pipeable Operator is essentially a pure function which takes one Observable as input and generates another Observable as output. Subscribing to the output Observable will also subscribe to the input Observable.

## Create

Creation Operators can be called as standalone functions to create a new Observable. For example: of(1, 2, 3) creates an observable that will emit 1, 2, and 3, one right after another.

## Higher-order Observables

Observables most commonly emit ordinary values like strings and numbers, but sometimes it is necessary to handle Observables of Observables. For example, imagine you had an Observable emitting strings that were the URLs of files you wanted to see. The code might look like this:

```typescript
const fileObservable = urlObservable.pipe(map((url) => http.get(url)));
```

http.get() returns an Observable (of string or string arrays probably) for each individual URL. Now you have an Observable of Observables, a higher-order Observable.

But how do you work with a higher-order Observable? Typically, by flattening. For example:

```typescript
const fileObservable = urlObservable.pipe(
  map((url) => http.get(url)),
  concatAll()
);
```

The concatAll() operator subscribes to each "inner" Observable that comes out of the "outer" Observable, and copies all the emitted values until that Observable completes, and goes on to the next one. All of the values are in that way concatenated. Other useful flattening operators can be used.


List of the most commonly used operators

## Creation operators

1. [Of](./operators/creation/of.md)
1. [From](./operators/creation/from.md)
1. [FromEvent](./operators/creation/from-event.md)

## Join Creation Operators

1. [CombineLatest](./operators/join-creation/combine-latest.md)
2. [Concat](./operators/join-creation/concat.md)

## Transformation Operators

1. [Map](./operators/transformation/map.md)
2. [SwitchMap](./operators/transformation/switch-map.md)

## Filtering Operators

1. [Debounce](./operators/filtering/debounce.md)
2. [DebounceTime](./operators/filtering/debounce-time.md)
3. [Distinct](./operators/filtering/distinct.md)
4. [DistinctUntilChanged](./operators/filtering/distinct-Until-Changed.md)
5. [DistinctUntilKeyChanged](./operators/filtering/distinct-until-key-changed.md)
6. [Filter](./operators/filtering/filter.md)
7. [First](./operators/filtering/first.md)
8. [TakeLast](./operators/filtering/take-last.md)
9. [TakeUntil](./operators/filtering/take-until.md)
10. [TakeWhile](./operators/filtering/take-while.md) 

## Join Operators

1. [CombineLatestAll](./operators/join/combine-latest-all.md)
2. [CombineLatestWith](./operators/join/combine-latest-with.md)
3. [ConcatWith](./operators/join/concat-with.md)

## Utility Operators

1. [Delay](./operators/utility/delay.md)
2. [Tap](./operators/utility/tap.md)  


find your operator
[https://rxjs-dev.firebaseapp.com/operator-decision-tree](https://rxjs-dev.firebaseapp.com/operator-decision-tree)
