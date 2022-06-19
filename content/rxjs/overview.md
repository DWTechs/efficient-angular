---
layout: default
title: Overview
permalink: /javascript/rxjs/overview/

---

You will mainly use observables to allow asynchronous transmission of messages between parts of your application.
In Angular you will use them via RxJS.

The essential concepts to solve async event management are:

- **Observable**: a function that can return several values over time. an invokable collection of future values or events. a lazy Push collections of multiple values. 
- **Observer**: a collection of callbacks that knows how to listen to values delivered by the Observable.
- **Subscription**: the execution of an Observable.
- **Operators**: pure functions that enable a functional programming style of dealing with collections with operations like map, filter, concat, reduce, etc.
- **Subject**: equivalent to an EventEmitter, and **the only way of multicasting a value or event to multiple Observers**.

An observable can provide several values of any type: literals, messages or events, depending on the context.
Both configuration and deletion logic are handled by the observable, so your application code only has to worry about subscribing and unsubscribing. 

In the Observer interface, there are three callback methods to handle the three types of notifications that an observable can send : 

1. **next** : required. A handler for each delivered value.
2. **error** : optional. A handler for an error notification. An error halts execution of the observable instance.
3. **complete** : optional. A handler for the execution-complete notification. Delayed values can continue to be delivered to the next handler after execution is complete.

## First example

Normally you register event listeners.

```Typescript
document.addEventListener('click', () => console.log('Clicked!'));
```

Using RxJS you create an observable instead, and subscribe to it.

```Typescript
import { fromEvent } from 'rxjs';

fromEvent(document, 'click').subscribe(() =>
    console.log('Clicked!')
);
```

## Purity

RxJS produces values using pure functions. Producing a code less prone to errors.

Normally you would create an impure function, where other pieces of your code can mess up your state.

```Typescript
let count = 0;
document.addEventListener('click', () => console.log(`Clicked ${++count} times`));
```

Using RxJS the state is isolated.

```Typescript
import { fromEvent } from 'rxjs';
import { scan } from 'rxjs/operators';

fromEvent(document, 'click')
  .pipe(scan(count => count + 1, 0))
  .subscribe(count => console.log(`Clicked ${count} times`)
);
```

## Flow

RxJS has a range of operators that helps control how the events flow through observables.

This is how you would allow at most one click per second, with plain JavaScript:

```Typescript

let count = 0;
let rate = 1000;
let lastClick = Date.now() - rate;
document.addEventListener('click', () => {
  if (Date.now() - lastClick >= rate) {
    console.log(`Clicked ${++count} times`);
    lastClick = Date.now();
  }
});
```

With RxJS:

```Typescript
import { fromEvent } from 'rxjs';
import { throttleTime, scan } from 'rxjs/operators';

fromEvent(document, 'click')
  .pipe(
    throttleTime(1000),
    scan(count => count + 1, 0)
  )
  .subscribe(count => console.log(`Clicked ${count} times`)
);
```

## Values

You can transform the values passed through your observables.

Here's how you can add the current mouse x position for every click, in plain JavaScript:

```Typescript
let count = 0;
const rate = 1000;
let lastClick = Date.now() - rate;
document.addEventListener('click', event => {
  if (Date.now() - lastClick >= rate) {
    count += event.clientX;
    console.log(count);
    lastClick = Date.now();
  }
});
```

With RxJS:

```Typescript
import { fromEvent } from 'rxjs';
import { throttleTime, map, scan } from 'rxjs/operators';

fromEvent(document, 'click')
  .pipe(
    throttleTime(1000),
    map(event => event.clientX),
    scan((count, clientX) => count + clientX, 0)
  )
  .subscribe(count => console.log(count));
```