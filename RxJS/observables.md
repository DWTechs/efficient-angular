---
layout: default
title: Creating observables
permalink: /javascript/rxjs/observables/

---


# Observables 

A lazy Push collections of multiple values.
It can be compared to other concepts like this :

|        | SINGLE	  | MULTIPLE       |
| ------ | -------- | -------------- |
| Pull	 | Function	| Iterator       |
| Push	 | Promise	| **Observable** |

Observables can return multiple values over time.

## Pull versus Push

Pull and Push are two different protocols that describe how a data Producer can communicate with a data Consumer.

- **In Pull systems**, the Consumer determines when it receives data from the data Producer. The Producer itself is unaware of when the data will be delivered to the Consumer.

  Every JavaScript Function is a Pull system. The function is a Producer of data, and the code that calls the function is consuming it by "pulling" out a single return value from its call.

- **In Push systems**, the Producer determines when to send data to the Consumer. The Consumer is unaware of when it will receive that data.

  Promises are the most common type of Push system. A Promise (the Producer) delivers a resolved value to registered callbacks (the Consumers), but unlike functions, it is the Promise which is in charge of determining precisely when that value is "pushed" to the callbacks.

## Push Multiple values with observables

Observables are a new Push system. It is a Producer of multiple values, "pushing" them to Observers (Consumers).

- A Function is a lazily evaluated computation that synchronously returns a single value on invocation.
- An iterator is a lazily evaluated computation that synchronously returns zero to (potentially) infinite values on iteration.
- A Promise is a computation that may (or may not) eventually return a single value asynchronously.
- An Observable is a lazily evaluated computation that can synchronously or asynchronously return zero to (potentially) infinite values from the time it's invoked onwards.


Observables are created using new Observable or a creation operator. They are subscribed to with an Observer. They execute to deliver next / error / complete notifications to the Observer. And their execution may be disposed.
These four aspects are all encoded in an Observable instance, but some of these aspects are related to other types, like Observer and Subscription.


# Create and Subscribe

Use the Observable constructor to create an observable. The constructor takes as its argument the subscriber function to run when the observable’s subscribe() method executes.
A subscriber function receives an Observer object, and can publish values to the observer's next() method.

Convention : observables are named with a "$" at the end

Example
```javascript
// This function runs when subscribe() is called
function sequenceSubscriber(observer: Observer<number>) {
  // synchronously deliver 1, 2, and 3, then complete
  observer.next(1);
  observer.next(2);
  observer.next(3);
  observer.complete();

  return {unsubscribe() {}};
}

// Create a new Observable that will deliver the above sequence
const sequence$ = new Observable(sequenceSubscriber);

// execute the Observable and print the result of each notification
sequence$.subscribe({
  next(num) { console.log(num); },
  complete() { console.log('Finished sequence'); }
});

// Logs:
// 1
// 2
// 3
// Finished sequence
```

See Observer for more info

## Disposing Observable Execution

Because Observable Executions may be infinite, and it's common for an Observer to want to abort execution in finite time, we need an API for canceling an execution. Since each execution is exclusive to one Observer only, once the Observer is done receiving values, it has to have a way to stop the execution, in order to avoid wasting computation power or memory resources.

When observable.subscribe is called, the Observer gets attached to the newly created Observable execution. This call also returns an object, the Subscription:

```javascript
const subscription = observable.subscribe(x =>  
  console.log(x)
);
```

The Subscription represents the ongoing execution, and has a minimal API which allows you to cancel that execution.

```typescript
import { from } from 'rxjs';

const observable$ = from([10, 20, 30]);
const subscription = observable$.subscribe(x => 
  console.log(x)
);

subscription$.unsubscribe();
```

See Subscription for more info
