---
layout: default
title: Basics
permalink: /javascript/angular/basics/

---

## Learn Typescript

All the Angular code snippets you will find online are written in Typescript. It is important that developers master it and always type the variables and objects they are working with.

### Use Typescript heritage

If a functionality related to a view is used on several screens, you can create a base component that contains its common functionality. The other components will be able to "extend" this base component.

## Learn Conventions

- variable name (camelCase):

```typescript
let variableName: string;
```

- observable name (camelCase):

```typescript
let observableName$: Observable<String>;
```

All variables must have a type.

## Learn MVVM pattern

MVVM architecture facilitates a separation of development of the GUI with the help of mark-up language or GUI code.
It is the acronym of : `Model/View/ViewModel`.

It is like MVC with subtle differences :
- In MVC, controller is the entry point to the Application, while in MVVM, the view is the entry point to the Application.
- In MVVM, the Model and the view are not linked.

### Model
The Model is the business data layer and is not linked to any specific graphical representation.
It stores data and related logic. It represents data that is being transferred between controller components or any other related business logic.

A single Model can notify several ViewModels of its change. Thus these Viewmodels will in turn notify their view to refresh.

### View
The View contains the structural definition of what users will see on the screen. It can contain static and dynamic content. It must not contain any application logic.
It stands for UI components like HTML, CSS, etc.

The View always receives user actions and only interacts with the ViewModel. The Model communicates with the server and notifies the ViewModel of its change.

The View is then no longer linked to the Model. Thus the ViewModel takes care of the entire Model change cycle. It carries out both the reception and the sending of the data to the View. This is called "data binding". The displayed information is linked between two entities and updated in real time.

It allows to decouple the different parts of the application by being able to make it evolve in a modular way.

### ViewModel
The ViewModel makes the link between the model and the view. It takes care of managing data links and possible conversions. This is where the binding comes in.
It is responsible for presenting functions, commands, methods, to support the state of the View.

The ViewModel takes care of :

- Presenting Model data to the View
- Receiving data changes from the View
- Asking the Model to change.


## Use Components

A component is a **reusable element** of the application, consisting of a view and a set of processes associated with this view. As shown in the code below, it is a class that exposes a view and defines the way the user can interact with it.

The component thus brings together the view and the associated business logic within the same entity.

They are the **keystone** of Angular. Think about your component before you start development.

Make the components small enough to be reusable elsewhere in the application, but don't overthink them because too small components only make the code more complex. It takes some experience and common sense to group components logically, but it quickly becomes natural.

When the component is identified, the input and output data must be documented.

## Use environment variables

The environment variables allow to modify the behavior of the application according to the environment. By default in Angular, they are stored in the src/environments folder. This folder contains two files:

- environment.ts, which contains the variables for the **development** mode
- environment.prod.ts, which contains the variables for the **production** mode.

The use of these vartiables makes it easier to put the application into production by avoiding any unnecessary manipluation before installation on the server.

## Use Reactive forms

In Angular, the same care has been applied to forms, and the framework gives a nice way to write forms. In fact, it gives us several ways!
You can either write your form using only directives in your template: that’s the **"template-driven"** way. From our experience, it shines when you have a simple form, with not much validation.

The other way is the **"code-driven"** way, where you will write a description of the form in your component, then use directives to bind this form to the inputs/textareas/selects in your template. It’s more verbose, but also more powerful, especially if you want to add custom validation, or to generate dynamic forms.

We encourage the use of the **code-driven** approach, more verbose but more powerful.

## Use Services

Put all the logic into services. The ViewModel should only contain code that is useful to the view.