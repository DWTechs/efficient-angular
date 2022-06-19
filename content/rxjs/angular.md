---
title: Angular
---

Angular makes use of observables as an interface to handle a variety of common asynchronous operations.


## HTTP

Angular’s HttpClient returns observables from HTTP method calls. For instance, http.get(‘/api’) returns an observable. This provides several advantages over promise-based HTTP APIs:

Observables do not mutate the server response (as can occur through chained .then() calls on promises). Instead, you can use a series of operators to transform values as needed.
HTTP requests are cancellable through the unsubscribe() method.
Requests can be configured to get progress event updates.
Failed requests can be retried easily.


## Router

Router.events provides events as observables. You can use the filter() operator from RxJS to look for events of interest, and subscribe to them in order to make decisions based on the sequence of events in the navigation process. 

The ActivatedRoute is an injected router service that makes use of observables to get information about a route path and parameters. For example, ActivatedRoute.url contains an observable that reports the route path or paths. 


## Reactive forms

Reactive forms have properties that use observables to monitor form control values. The FormControl properties valueChanges and statusChanges contain observables that raise change events. Subscribing to an observable form-control property is a way of triggering application logic within the component class. 

Example:
FormGroup contains one or more FormControls. In this example, we get the FormControl called "name". Then we integrate the new value in the array at each change
```javascript
import { FormGroup } from '@angular/forms';

@Component({
  selector: 'my-component',
  template: 'MyComponent Template'
})
export class MyComponent implements OnInit {
  nameChangeLog: string[] = [];
  heroForm!: FormGroup;

  ngOnInit() {
    this.logNameChange();
  }
  logNameChange() {
    const nameControl = this.heroForm.get('name');
    nameControl?.valueChanges.subscribe(
      (value: string) => this.nameChangeLog.push(value)
    );
  }
}
```


## AsyncPipe 

The async pipe subscribes to an Observable or Promise and returns the latest value it has emitted. When a new value is emitted, the async pipe marks the component to be checked for changes. When the component gets destroyed, the async pipe unsubscribes automatically to avoid potential memory leaks.

Example
This example binds a Promise to the view. Clicking the Resolve button resolves the promise.

```javascript
@Component({
  selector: 'async-promise-pipe',
  template: `<div>
    <code>promise|async</code>:
    <button (click)="clicked()">button</button>
    <span>Wait for it... {{ greeting | async }}</span>
  </div>`
})
export class AsyncPromisePipeComponent {
  greeting: Promise<string>|null = null;
  arrived: boolean = false;

  private resolve: Function|null = null;

  constructor() {
    this.reset();
  }

  reset() {
    this.arrived = false;
    this.greeting = new Promise<string>((resolve, reject) => {
      this.resolve = resolve;
    });
  }

  clicked() {
    if (this.arrived) {
      this.reset();
    } else {
      this.resolve!('hi there!');
      this.arrived = true;
    }
  }
}
```


It's also possible to use async with Observables. The example below binds the time Observable to the view. The Observable continuously updates the view with the current time.

```javascript
@Component({
  selector: 'async-observable-pipe',
  template: `<div><code>observable|async</code>:
       Time: {{ time | async }}</div>`
})
export class AsyncObservablePipeComponent {
  time = new Observable<string>(observer => {
    setInterval(() => observer.next(new Date().toString()), 1000);
  });
}
```

## All subscriptions must be deleted

```typescript
getVehicle(idVehicle: number): void {
    // get the vehicle detail by id
    this.vehicleSubscribe = this.vehicleWebService.get(idVehicle).subscribe((vehicle) => {
      this.vehicle = vehicle;
    });
  }

ngOnDestroy() {
    if(this.vehicleSubscribe){
        this.vehicleSubscribe.unsubscribe();
    }
  }
```

Note that HttpClient requests are automatically unsubscribed once the response has been sent. So you do not need to manually unsubscribe it.