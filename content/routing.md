---
layout: default
title: Routing
permalink: /javascript/angular/routing/
---

The Angular Router is an optional service that presents a particular component view for a given URL.
It isn't part of the Angular core and thus is in its own library package, **@angular/router**.

```typescript
import { RouterModule, Routes } from '@angular/router';
```

## Configuration
A router has no routes until you configure it. The following example creates five route definitions, configures the router via the RouterModule.forRoot() method, and adds the result to the imports array of the AppModule'.

There are two methods of RouterModule: 
- **forRoot()**\
  The **forRoot** static method is the method that configures the root routing module for your app. When you call **RouterModule.forRoot(routes)**, you are asking Angular to instantiate an instance of the Router class globally. Just like Angular creates a new base AppModule to import all of your feature modules, it also provides the AppRoutingModule to import all of your child routes.\
  In the new app that you have created via the Angular CLI, the forRoot method is actually already being used inside of the app-routing.module.ts. In your app, you only want to use the forRoot method once. This is because this method tells Angular to instantiate an instance of the Router class under the hood, and there can be only one router in your app. The forRoot static method is a part of a pattern that ensures that you are using singleton classes.
  ```typescript
  const routes: Routes = [
    { path: <pathname>, component: <component> },
      ...
  ];

  @NgModule({
    imports: [
      RouterModule.forRoot(routes)
    ],
    ...
  })

  export class AppModule { }
  ```
- **forChild()**\
  The forChild method is the method that you will call to register routes throughout your app and you will use it inside of the child, routing modules that you create.
  ```typescript
  const routes: Routes = [
    { 
      path:  <parent-pathname>,
        component:  <parent-component>,
        children: [
            {
                path:  <child-pathname>,
                component: <child-component> 
            }
        ]
    }
  ];
  ```



## Directives
### RouterLink
When applied to an element in a template, makes that element a link that initiates navigation to a route.

#### Examples
1. **Static** link
```html
<a routerLink="/user">link to user component</a>
```
OR
```html
<a routerLink="/user/bob">  link to user component</a>
```
2. If you use **dynamic** values to generate a link, you can pass the array of path segments, followed by the parameters for each segment. Line below generates a link to */team/11/user/bob;details=true*
```html
<a routerLink="['/team', teamId, 'user', userName, {details: true}]">
  link to user component
</a>
```
3. To pass the **query parameters**, you can write the anchor tag. Line below generates a link to *//user/bob?debug=true#education*
```html
<a routerLink="['/user/bob']" queryParams="{debug: true}" fragment="education">
  link to user component
</a>
```

### RouterLinkActive
Tracks whether the linked route of an element is currently active, and allows you to specify one or more CSS classes to add to the element when the linked route is active.

#### Example
```html
<a routerLink="/user/bob" routerLinkActive="active">Bob</a>
```

### RouterLinkOutlet
Acts as a placeholder that Angular dynamically fills based on the current router state.
\
\
Each outlet can have a unique name, determined by the optional name attribute. The name cannot be set or changed dynamically. If not set, default value is "primary".
```html
<router-outlet></router-outlet>
<router-outlet name='left'></router-outlet>
<router-outlet name='right'></router-outlet>
```
Named outlets can be the targets of secondary routes. The Route object for a secondary route has an outlet property to identify the target outlet:
```typescript
{path: <pathname>, component: <component>, outlet: <target_outlet_name>}
```