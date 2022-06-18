---
layout: default
title: Basics
permalink: /javascript/angular/basics/

---

## Learn NPM

[https://www.npmjs.com/](https://www.npmjs.com/)

## Learn Typescript

All the Angular code snippets you will find online are written in Typescript. It is important that developers master it and always type the variables and objects they are working with.

## Learn Conventions

- variable name (camelCase):

```typescript
let nameVariable: string;
```

- observable name (camelCase):

```typescript
let nameObservable$: Observable<String>;
```

All variables must have a type

## Use environment variables

The environment variables allow to modify the behavior of the application according to the environment. By default on angular, they are stored in the src/environments folder. This folder contains two files:

- environment.ts, which contains the variables for the **development** mode
- environment.prod.ts, which contains the variables for the **production** mode.

The use of these vartiables makes it easier to put the application into production by avoiding any unnecessary manipluation before installation on the server.

## Learn MVVM pattern

The Model: This is the business data layer and is not linked to any specific graphical representation.

- The View: It contains the structural definition of what users will see on the screen. It can contain static and dynamic content (animations and change states). It must not contain any application logic.

- The View - Model: This component makes the link between the model and the view. It takes care of managing data links and possible conversions. This is where the binding comes in.

MVVM is the acronym of : `Model/View/View-Model`.

The View always receives user actions and only interacts with the Model-View. The Model communicates with the server and notifies the Model View of its change.

The Model View takes care of :

- Presenting Model data to the View
- Receiving data changes from the View
- Asking the Model to change.

The View is then no longer linked to the Model. Thus the Model-View takes care of the entire Model change cycle. It carries out both the reception and the sending of the data to the View. This is called "data binding". The displayed information is linked between two entities and updated in real time.

This last mechanism is the key to the MVVM pattern. It allows us to decouple the different parts of our application by being able to make it evolve in a modular way.

A single Model can notify several Model Views of its change. Thus these Model Views will in turn notify their view to refresh.

## Use Components

A component is a **reusable element** of the application, consisting of a view and a set of processes associated with this view. As shown in the code below, it is a class that exposes a view and defines the way the user can interact with it.

The component thus brings together the view and the associated business logic within the same entity. This is a fundamental difference with AngularJS where the two logics are clearly separated and the business logic contained in the controller.

Many similarities exist between Angular 2 components and AngularJS directives. Indeed, AngularJS directives also contain a view and associated processing. However, the Angular 2 components are independent.

Angular 2 therefore simplifies the architecture of an AngularJS application, by gathering in a single entity the concepts of controller, scope and view: the component.

The directives still exist but they no longer contain a template and only allow you to remove or associate a particular behavior to a DOM element. Example: ngIf, ngFor

## Think Components

The components are the **keystone** of Angular. Think about your component before you start development: the list of questions to answer before developing a new component can be found in the `"development > Practices"` section.

Make the components small enough to be reusable elsewhere in the application, but don't oversize them because too small components only make the code more complex. It takes some experience and common sense to group components logically, but it quickly becomes natural.

When the component is identified, the input and output data must be documented.

## Use Typescript heritage

If a functionality related to a view is used on several screens, you can create a base component that contains its common functionality. The other components will be able to "extend" this base component.

## Use Reactive forms

In Angular, the same care has been applied to forms, and the framework gives us a nice way to write our forms. In fact, it gives us several ways!
You can either write your form using only directives in your template: that’s the **"template-driven"** way. From our experience, it shines when you have a simple form, with not much validation.

The other way is the **"code-driven"** way, where you will write a description of the form in your component, then use directives to bind this form to the inputs/textareas/selects in your template. It’s more verbose, but also more powerful, especially if you want to do add custom validation, or to generate dynamic forms.

We encourage the use of the **code-driven** approach, more verbose but more powerful.


## Use Services

Put all the logic into services. The model view should only contain code that is useful to the view