---
layout: default
title: BehaviorSubject
permalink: /javascript/rxjs/subscription/

---


# Subscription

an object that represents a disposable resource, usually the execution of an Observable. A Subscription has one important method, unsubscribe, that takes no argument and just disposes the resource held by the subscription.

```typescript
import { interval } from 'rxjs';

const observable = interval(1000);
const subscription = observable.subscribe(x => console.log(x));
// Later:
// This cancels the ongoing Observable execution which
// was started by calling subscribe with an Observer.
subscription.unsubscribe();
```

Subscriptions can also be put together, so that a call to an unsubscribe() of one Subscription may unsubscribe multiple Subscriptions. You can do this by "adding" one subscription into another:

```typescript
import { interval } from 'rxjs';
 
const observable1 = interval(400);
const observable2 = interval(300);
 
const subscription = observable1.subscribe(x => console.log('first: ' + x));
const childSubscription = observable2.subscribe(x => console.log('second: ' + x));
 
subscription.add(childSubscription);
 
setTimeout(() => {
  // Unsubscribes BOTH subscription and childSubscription
  subscription.unsubscribe();
}, 1000);
```

Subscriptions also have a remove(otherSubscription) method, in order to undo the addition of a child Subscription.

The unsubscribe method will therefore :
1. unregister the callbacks: next, error and complete
2. destroy the Observable (interrupt the processing done by the Observable)
3. possibly free the memory if they are not referenced elsewhere.

The unsubscribe is generally done :
- when a component is destroyed via the ngOnDestroy lifecycle hook.
- when an Observable has to replace another one (e.g. : launching a new search by a user or refreshing the content).