---
title: CombineLatestWith
---

Create an observable that combines the latest values from all passed observables and the source into arrays and emits them.


## Syntax 

```javascript
combineLatestWith<T, A extends readonly unknown[]>(...otherSources: any[]): OperatorFunction<T, Cons<T, A>>
```

| Parameters | Description |
| ---------- | ----------- |
| otherSources | the other sources to subscribe to. |


## Returns

OperatorFunction<T, Cons<T, A>>: A function that returns an Observable that emits the latest emissions from both source and provided Observables.


## Example

Simple calculation from two inputs.

```javascript
// Setup: Add two inputs to the page
const input1 = document.createElement('input');
document.body.appendChild(input1);
const input2 = document.createElement('input');
document.body.appendChild(input2);
 
// Get streams of changes
const input1Changes$ = fromEvent(input1, 'change');
const input2Changes$ = fromEvent(input2, 'change');
 
// Combine the changes by adding them together
input1Changes$.pipe(
  combineLatestWith(input2Changes$),
  map(([e1, e2]) => Number(e1.target.value) + Number(e2.target.value)),
)
.subscribe(x => console.log(x));
```