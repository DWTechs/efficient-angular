---
layout: default
title: Interceptors
permalink: /javascript/angular/interceptors/
---

Interceptors are used in Angular to intercept and handle an **HttpRequest** and **HttpResponse**.

To add some specific headers or params in our request or say modify my HttpRequest or HttpResponse, rather than handling it separately for each of my requests angular generally provides us interceptors. They are written once and intercepted by all our requests and response using the HttpClient.

By intercepting the HTTP request, we can modify or change the value of the request.

To create an Interceptor, we need to implement the **HttpInterceptor** interface from *@angular/common/http*. Every time our application makes an HTTP request using the **HttpClient** service, the Interceptor calls the **intercept()** method.

When the **intercept()** is called Angular passes a reference to the **httpRequest** object. With this request, we can inspect it and modify it as necessary. Once our logic is complete, we call **next.handle** and return the updated request to the application.

```typescript
intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>>
```
| Parameter | Description |
| ---- | ---- |
| req | The outgoing request object to handle.
| next | The next interceptor in the chain, or the backend if no interceptors remain in the chain.



## Providing HTTP Interceptors
Like any other service, we can’t use an interceptor, unless we provide it to the application. However, interceptors are provided differently than ordinary services. They need to be provided in a NgModule.

```typescript
import { HTTP_INTERCEPTORS } from '@angular/common/http';
// Rest imports...

@NgModule({
   declarations: [AppComponent],
   imports: [
      // ...
   ],
   providers: [
      { provide: HTTP_INTERCEPTORS, useClass: LogInterceptor, multi: true },
      { provide: HTTP_INTERCEPTORS, useClass: CacheInterceptor, multi: true },
      { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true },
      { provide: HTTP_INTERCEPTORS, useClass: MockInterceptor, multi: true },
   ],
   bootstrap: [AppComponent],
})
export class AppModule {}
```

## Interceptor order
An important detail is that interceptors are applied in the order they are provided. In other words, order matters.Requests are processed in the order we provide the interceptors, while responses are processed in the opposite order.

For example, in the previous snippet, the order of processing for requests is: **LogInterceptor > CacheInterceptor > AuthInterceptor > MockInterceptor**, while the order of processing for responses is the opposite: **MockInterceptor > AuthInterceptor > CacheInterceptor > LogInterceptor**.

## Example

Apps often use an interceptor to set default headers on outgoing requests.

Here is its **AuthInterceptor** that injects that service to get the token and adds an authorization header with that token to every outgoing request:

```typescript
@Injectable()
export class AuthInterceptor implements HttpInterceptor {

  constructor() {}

  intercept(req: HttpRequest<any>, next: HttpHandler) {
    const authToken = 'auth-token';

    // Clone the request and replace the original headers with
    // cloned headers, updated with the authorization.
    const authReq = req.clone({
      headers: req.headers.set('Authorization', authToken)
    });

    // send cloned request with header to the next handler.
    return next.handle(authReq);
  }
}
```
The practice of cloning a request to set new headers is so common that there's a setHeaders shortcut for it:
```typescript
// Clone the request and set the new header in one step.
const authReq = req.clone({ setHeaders: { Authorization: authToken } });
```
Register created interceptor:
```typescript
@NgModule({
  // ...
  providers: [ 
    { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true },
  ],
})
export class AppModule { }
```
## Useful links
- [Complete guide with an example](https://javascript.plainenglish.io/angular-interceptors-a-complete-guide-7294e2317ecf)
- [Http guide](https://angular.io/guide/http#intercepting-requests-and-responses) 