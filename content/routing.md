---
layout: default
title: Routing
permalink: /javascript/angular/routing/
---

The Angular Router is an optional service that presents a particular component view for a given URL.
It isn't part of the Angular core and thus is in its own library package, **@angular/router**.

```typescript
import { RouterModule, Routes } from "@angular/router";
```

## Configuration

A router has no routes until you configure it. The following example creates five route definitions, configures the router via the RouterModule.forRoot() method, and adds the result to the imports array of the AppModule'.

There are two methods of RouterModule:

- **forRoot()**\
  The **forRoot** static method is the method that configures the root routing module for your app. When you call **RouterModule.forRoot(routes)**, you are asking Angular to instantiate an instance of the Router class globally. Just like Angular creates a new base AppModule to import all of your feature modules, it also provides the AppRoutingModule to import all of your child routes.\
  If you create an app via the Angular CLI, the forRoot method is actually already being used inside of the app-routing.module.ts. In your app, you only want to use the forRoot method once. This is because this method tells Angular to instantiate an instance of the Router class under the hood, and there can be only one router in your app. The forRoot static method is a part of a pattern that ensures that you are using singleton classes.

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
  ### Example
  Let's say we have an app with routes for:

  - User
    - Register
    - List
    - Delete
  - Company
    - Register
    - List
    - Delete
    
  You could use the mentioned methods like this:\
  **app-routing.module.ts**
  ```typescript
  const  routes: Routes = [
    {
      path: 'user', loadChildren: './user/user.module#userModule'
      // this lazy loading is deprecated in favor of
      // loadChildren: () => import('./user/user.module').then(m => m.UserModule) }
    },
    // same deprecation applies here
    { path: 'company', loadChildren: './company/company.module#CompanyModule'},
    // same deprecation applies here
    { path: '**', loadChildren: './page-not-found/page-not-found.module#PageNotFoundModule'}
  ];

  @NgModule({
    imports: [RouterModule.forRoot(routes)],
    exports: [RouterModule]
  })
  export class AppRoutingModule { }
  ```
  **user-routing.module.ts**\
  And the relative routes to *user/* and *company/* are registered using RouterModule#forChild
  ```typescript
  const routes: Routes = [
    { path: 'list', component: UserComponent},
    { path: 'delete/:id', component: UserDeleteComponent},
    { path: 'register/:id', component: UserRegisterComponent},
  ];

  @NgModule({
    imports: [ RouterModule.forChild(routes) ],
    exports: [ RouterModule ]
  })
  ```
  And the same would go on for the Company children routes.

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
<a routerLink="/user/bob"> link to user component</a>
```

2. If you use **dynamic** values to generate a link, you can pass the array of path segments, followed by the parameters for each segment. Line below generates a link to _/team/11/user/bob;details=true_

```html
<a routerLink="['/team', teamId, 'user', userName, {details: true}]">
  link to user component
</a>
```

3. To pass the **query parameters**, you can write the anchor tag. Line below generates a link to _//user/bob?debug=true#education_

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
Router-outlet in Angular works as a placeholder which is used to load the different components dynamically based on the activated component or current route state. Navigation can be done using router-outlet directive and the activated component will take place inside the router-outlet to load its content.
```html
<router-outlet></router-outlet>
```
Each outlet can have a unique name, determined by the optional name attribute. The name cannot be set or changed dynamically. If not set, default value is "primary".

```html
<router-outlet></router-outlet>
<router-outlet name="left"></router-outlet>
<router-outlet name="right"></router-outlet>
```

Named outlets can be the targets of secondary routes. The Route object for a secondary route has an outlet property to identify the target outlet:

```typescript
{path: <pathname>, component: <component>, outlet: <target_outlet_name>}
```
