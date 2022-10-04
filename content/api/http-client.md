---
layout: default
title: HttpClient
permalink: /javascript/angular/api/http-client/
---

HttpClient is used to make HTTP requests, like GET | POST | PUT | DELETE to back end server.

## Setup for server communication
Start by importing the HttpClientModule module from the @angular/common/http package:
```typescript
import { HttpClientModule } from '@angular/common/http';
```
Next, add the HttpClientModule module to the imports array of the AppModule:
```typescript
@NgModule({
  imports: [
    ...
    HttpClientModule,
    ...
  ],
  ...
})
export class AppModule { }
```

## Methods
### GET
HttpClient.**get()** constructs an observable that, when subscribed, causes the configured PUT request to execute on the server.\
It takes two arguments:
1. Resource URL
2. Options
Options parameter object used to configure various Http request options like request headers,parameters and response type etc.

And this parameter is optional.
```
options: {
    headers?: HttpHeaders | {[header: string]: string | string[]},
    observe?: 'body' | 'events' | 'response',
    params?: HttpParams|{[param: string]: string | number | boolean | ReadonlyArray<string | number | boolean>},
    reportProgress?: boolean,
    responseType?: 'arraybuffer'|'blob'|'json'|'text',
    withCredentials?: boolean,
}
```
### POST
HttpClient.**post()** constructs an observable that, when subscribed, causes the configured PUT request to execute on the server.\
Method **post()** is similar to **get()** in that it has a type parameter, which you can use to specify that you expect the server to return data of a given type. The method takes a resource URL and two additional parameters:

```
post(
    url: string,
    body?: any,
    options: {
        headers?: HttpHeaders | { [header: string]: string | string[]},
        context?: HttpContext,
        observe?: 'body' | 'events' | 'response',
        params?: HttpParams|{[param: string]: string | number | boolean | ReadonlyArray<string | number | boolean>},
        reportProgress?: boolean,
        responseType: "arraybuffer",
        withCredentials?: boolean
    }
)
```
Apps often send data to a server with a POST request when submitting a form.

### PUT
HttpClient.**put()** constructs an observable that, when subscribed, causes the configured PUT request to execute on the server. It has the same parameters as **post()**. 
### DELETE
HttpClient.**delete()** constructs an observable that, when subscribed, causes the configured DELETE request to execute on the server.
```
delete(
    url: string,
    options: {
        headers?: HttpHeaders | { [header: string]: string | string[]},
        context?: HttpContext,
        observe?: 'body' | 'events' | 'response',
        params?: HttpParams|{[param: string]: string | number | boolean | ReadonlyArray<string | number | boolean>},
        reportProgress?: boolean,
        responseType: "arraybuffer",
        withCredentials?: boolean,
        body?: any
    }
)
```
## Example
Let's write an example how to send add, get, delete and update data on the server: 
Firstly, in **.service.ts** write methods to send GET, POST, DELETE and PUT requests.
```typescript
import { Injectable } from '@angular/core';
import { HttpClient, HttpHeaders } from '@angular/common/http';

import { Observable} from 'rxjs';
import { catchError } from 'rxjs/operators';

import { User } from './user';

@Injectable({ providedIn: 'root' })
export class UserService {

  private url = 'api/users';  // URL to web api

  httpOptions = {
    headers: new HttpHeaders({ 'Content-Type': 'application/json' })
  };

  constructor(
    private http: HttpClient) { }

  /** GET users from the server */
  getUsers(): Observable<User[]> {
    return this.http.get<User[]>(this.url)
      .pipe(
        catchError(this.handleError<User[]>('getUsers', []))
      );
  }

  /** GET user by id*/
  getUser(id: number): Observable<User> {
    const urlWithID = `${this.url}/${id}`;
    return this.http.get<User>(urlWithID).pipe(
      catchError(this.handleError<User>(`getUser id=${id}`))
    );
  }
  
  /** POST: add a new user to the server */
  addUser(user: User): Observable<User> {
    return this.http.post<User>(this.url, user, this.httpOptions).pipe(
      catchError(this.handleError<User>('addUser'))
    );
  }

  /** DELETE: delete the user from the server */
  deleteUser(id: number): Observable<User> {
    const urlWithID = `${this.url}/${id}`;
    return this.http.delete<User>(urlWithID, this.httpOptions).pipe(
      catchError(this.handleError<User>('deleteUser'))
    );
  }

  /** PUT: update the user on the server */
  updateUser(user: User): Observable<any> {
    return this.http.put(this.url, user, this.httpOptions).pipe(
      catchError(this.handleError<any>('updateUser'))
    );
  }
}
```
Then in **.component.ts** write initiatialization operations by subscribing to the Observable returned by those service methods.

```typescript
import { Component, OnInit } from '@angular/core';

import { User } from '../user';
import { UserService } from '../user.service';

@Component({
  selector: 'app-users',
  templateUrl: './user.component.html',
  styleUrls: ['./user.component.css']
})
export class UserComponent implements OnInit {
  users: User[] = [];

  constructor(private userService: UserService) { }

  ngOnInit(): void {
    this.getUsers();
  }

  getUsers(): void {
    this.userService.getUsers()
    .subscribe(users => this.users = users);
  }

  add(newUser: User): void {
    this.userService
    .addUser(newUser)
    .subscribe(user => this.users.push(user));
  }

  delete(id: number): void {
    this.userService.deleteUser(id).subscribe();
  }

  update(user: User): void {
    this.userService
    .updateUser(user)
    .subscribe(user => {
        // find index of current user in this.users
        const index = this.users.findIndex(u => u.id === user.id);
        // replace exist user into updated
        this.users[index] = user;
    })
  }

}
