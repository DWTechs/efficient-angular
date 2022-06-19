---
title: Actions
---

Actions are one of the main building blocks in NgRx. Actions express unique events that happen throughout your application. From user interaction with the page, external interaction through network requests, and direct interaction with device APIs, these and more events are described with actions.

Actions are the inputs and outputs of many systems in NgRx. Actions help you to understand how events are handled in your application.


## The Action interface

An Action in NgRx is made up of a simple interface:
```javascript
interface Action {
  type: string;
}
```
 
The type property is for describing the action that will be dispatched in your application. The value of the type comes in the form of [Source] Event and is used to provide a context of what category of action it is, and where an action was dispatched from. 
You add properties to an action to provide additional context or metadata for an action.

Listed below are examples of actions written as plain old JavaScript objects (POJOs):

```javascript
{
  type: '[Auth API] Login Success'
}
```
This action describes an event triggered by a successful authentication after interacting with a backend API.

```javascript
{
  type: '[Login Page] Login',
  username: string;
  password: string;
}
```
This action describes an event triggered by a user clicking a login button from the login page to attempt to authenticate a user. The username and password are defined as additional metadata provided from the login page.


## Writing actions

There are a few rules to writing good actions within your application.

**Upfront** - write actions before developing features to understand and gain a shared knowledge of the feature being implemented.
**Divide** - categorize actions based on the event source.
**Many** - actions are inexpensive to write, so the more actions you write, the better you express flows in your application.
**Event-Driven** - capture events not commands as you are separating the description of an event and the handling of that event.
**Descriptive** - provide context that are targeted to a unique event with more detailed information you can use to aid in debugging with the developer tools.

Let's look at an example action of initiating a login request.

login-page.actions.ts
```javascript
import { createAction, props } from '@ngrx/store';

export const login = createAction(
  '[Login Page] Login',
  props<{ username: string; password: string }>()
);
```
The createAction function returns a function, that when called returns an object in the shape of the Action interface. The props method is used to define any additional metadata needed for the handling of the action. Action creators provide a consistent, type-safe way to construct an action that is being dispatched.

Use the action creator to return the Action when dispatching.

login-page.component.ts
```javascript
onSubmit(username: string, password: string) {
  store.dispatch(login({ username: username, password: password }));
}
```
The login action creator receives an object of username and password and returns a plain JavaScript object with a type property of [Login Page] Login, with username and password as additional properties.

The returned action has very specific context about where the action came from and what event happened.

The category of the action is captured within the square brackets [].
The category is used to group actions for a particular area, whether it be a component page, backend API, or browser API.
The Login text after the category is a description about what event occurred from this action. In this case, the user clicked a login button from the login page to attempt to authenticate with a username and password.