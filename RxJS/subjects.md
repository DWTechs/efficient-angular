---
layout: default
title: BehaviorSubject
permalink: /javascript/rxjs/subjects/

---


# Subjects

It is the big thing of RxJS as it gives multicast abilities to observables.

**It allows values to be multicasted to many Observers**. While plain Observables are unicast.

- Every Subject is an Observable. Given a Subject, you can subscribe to it, providing an Observer, which will start receiving values normally. From the perspective of the Observer, it cannot tell whether the Observable execution is coming from a plain unicast Observable or a Subject.

  Internally to the Subject, subscribe does not invoke a new execution that delivers values. It simply registers the given Observer in a list of Observers, similarly to how addListener works.

- Every Subject is an Observer. It is an object with the methods next(v), error(e), and complete(). To feed a new value to the Subject, just call next(theValue), and it will be multicasted to the Observers registered to listen to the Subject.

```typescript
import { Subject } from 'rxjs';
 
const subject = new Subject<number>();

// Observer A
subject.subscribe({
  next: (v) => console.log(`observerA: ${v}`)
});

// Observer 2
subject.subscribe({
  next: (v) => console.log(`observerB: ${v}`)
});
 
subject.next(1);
subject.next(2);
 
// Logs:
// observerA: 1
// observerB: 1
// observerA: 2
// observerB: 2
```

Since a Subject is an Observer, this also means you may provide a Subject as the argument to the subscribe of any Observable

```typescript
import { Subject, from } from 'rxjs';
 
const subject = new Subject<number>();
 
// Observer A
subject.subscribe({
  next: (v) => console.log(`observerA: ${v}`)
});

// Observer B
subject.subscribe({
  next: (v) => console.log(`observerB: ${v}`)
});
 
const observable = from([1, 2, 3]);

// You can subscribe providing a Subject
observable.subscribe(subject); 
 
// Logs:
// observerA: 1
// observerB: 1
// observerA: 2
// observerB: 2
// observerA: 3
// observerB: 3
```

With the approach above, we essentially just converted a unicast Observable execution to multicast, through the Subject. This demonstrates how **Subjects are the only way of making any Observable execution be shared to multiple Observers**.


There are also a few specializations of the Subject type like BehaviorSubject, ReplaySubject.

## BehaviorSubject

It has a notion of "the current value".
It stores the latest value emitted to its consumers, and whenever a new Observer subscribes, it will immediately receive the "current value" from the BehaviorSubject.

BehaviorSubjects are useful for representing "values over time".

In the following example, the BehaviorSubject is initialized with the value 0 which the first Observer receives when it subscribes. The second Observer receives the value 2 even though it subscribed after the value 2 was sent.

```typescript
import { BehaviorSubject } from 'rxjs';

// 0 is the initial value
const subject = new BehaviorSubject(0);
 
subject.subscribe({
  next: (v) => console.log(`observerA: ${v}`)
});
 
subject.next(1);
subject.next(2);
 
subject.subscribe({
  next: (v) => console.log(`observerB: ${v}`)
});
 
subject.next(3);
 
// Logs
// observerA: 0
// observerA: 1
// observerA: 2
// observerB: 2
// observerA: 3
// observerB: 3
```

BehaviorSubject has 3 specific features:

1. It needs an initial value as it must always return a value on subscription even if it hasn't received a next().
2. Upon subscription, it returns the last value of the subject.
3. At any point, you can retrieve its last value using the getValue() method.

## ReplaySubject

A ReplaySubject is similar to a BehaviorSubject in that it can send old values to new subscribers, but it can also record a part of the Observable execution.

A ReplaySubject records multiple values from the Observable execution and replays them to new subscribers.

When creating a ReplaySubject, you can specify how many values to replay:

```javascript
import { ReplaySubject } from 'rxjs';

// buffer 3 values for new subscribers
const subject = new ReplaySubject(3); 
 
// Observer A
subject.subscribe({
  next: (v) => console.log(`observerA: ${v}`)
});
 
subject.next(1);
subject.next(2);
subject.next(3);
subject.next(4);
 
// Observer B
subject.subscribe({
  next: (v) => console.log(`observerB: ${v}`)
});
 
subject.next(5);
 
// Logs:
// observerA: 1
// observerA: 2
// observerA: 3
// observerA: 4
// observerB: 2
// observerB: 3
// observerB: 4
// observerA: 5
// observerB: 5
```


You can also specify a window time in milliseconds, besides of the buffer size, to determine how old the recorded values can be. In the following example we use a large buffer size of 100, but a window time parameter of just 500 milliseconds.

```javascript
import { ReplaySubject } from 'rxjs';

const subject = new ReplaySubject(100, 500);
 
// Observer A
subject.subscribe({
  next: (v) => console.log(`observerA: ${v}`)
});
 
let i = 1;
setInterval(() => subject.next(i++), 200);
 
setTimeout(() => {
  // Observer B
  subject.subscribe({
    next: (v) => console.log(`observerB: ${v}`)
  });
}, 1000);
 
// Logs
// observerA: 1
// observerA: 2
// observerA: 3
// observerA: 4
// observerA: 5
// observerB: 3
// observerB: 4
// observerB: 5
// observerA: 6
// observerB: 6
// ...
```


## Subject vs BehaviorSubject vs ReplaySubject


1. **Subject** - a subscriber will only get published values that were emitted after the subscription. Does the subscriber need to know anything about previous values? If not, then you can use this. 
For example, with component-to-component communication. Say you have a component that publishes events for other components on a button click. You can use a service with a subject to communicate.

2. **BehaviorSubject** - the last value is cached. A subscriber will get the latest value upon initial subscription. The semantics for this subject is to represent a value that changes over time. For example a logged in user. The initial user might be an anonymous user. But once a user logs in, then the new value is the authenticated user state.
The BehaviorSubject is initialized with an initial value. 

3. **ReplaySubject** - it can cache up to a specified number of emissions. Any subscribers will get all the cached values upon subscription.

## Void subject

Sometimes the emitted value doesn't matter as much as the fact that a value was emitted.

For instance, the code below signals that one second has passed.

```typescript
const subject = new Subject<void>();
setTimeout(() => subject.next(), 1000);
```

By declaring a void subject, you signal that the value is irrelevant. Only the event itself matters.
