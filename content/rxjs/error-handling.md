---
layout: default
title: Error handling
permalink: /javascript/rxjs/errorhandling/

---

You handle errors by specifying an error callback on the observer. Producing an error also causes the observable to clean up subscriptions and stop producing values.

```javascript
myObservable.subscribe({
  next(num) { console.log('Next num: ' + num)},
  error(err) { console.log('Received an error: ' + err)}
});
```

RxJS provides the catchError operator that lets you handle known errors in the observable recipe.
For example, when an error is generated, if you detect this error and provide a default value, your flow continues to process the values.

Use the retry operator before the catchError operator. It resubscribes to the original source observable, which can then re-run the full sequence of actions that resulted in the error.

Example
```javascript
// Return "response" from the API.
const apiData = ajax('/api/data').pipe(
  map((res: any) => {
    if (!res.response) {
      throw new Error('Value expected!');
    }
    return res.response;
  }),
  retry(3), // Retry up to 3 times before failing
  catchError(() => of([])) // If an error happens, return an empty array.
);
```