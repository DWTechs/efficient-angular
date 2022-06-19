---
layout: default
title: Observer
permalink: /javascript/rxjs/observer/

---

A consumer of values delivered by an Observable. Observers are simply a set of callbacks, one for each type of notification delivered by the Observable: next, error, and complete. The following is an example of a typical Observer object:

```typescript
const observer = {
  next: x => console.log('Observer got a next value: ' + x),
  error: err => console.error('Observer got an error: ' + err),
  complete: () => console.log('Observer got a complete notification'),
};
```

To use the Observer, provide it to the subscribe of an Observable:

```typescript
observable.subscribe(observer);
```

Observers are objects with three callbacks, one for each type of notification that an Observable may deliver.

When subscribing to an Observable, you may also just provide the next callback as an argument, without being attached to an Observer object, for instance like this:

```typescript
observable.subscribe(x => console.log('Observer got a next value: ' + x));
```