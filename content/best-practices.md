---
layout: default
title: Best Practices
permalink: /javascript/angular/best-practices/

---

## Structure and naming

Structure your application in order to : 
- Locate code quickly. Locating the code must be intuitive and fast. This is really important when someone else will have to work on the application.
- Identify code at a glance. Name the file such that you instantly know what it contains and represents. Prefer long and descriptive names over abbreviations that makes no sense.
- Keep the flattest structure you can. The structure must be as flat as possible. It is much easier to search through a folder containing some files than a folder containing subfolders. Above 7 files, the human eyes will have some difficulties to scan the folder, in that case you can create subfolders.
- Do not repeat yourself. Do not be redundant in file names. For example no need to call a component "product-view.component.html", the .html extension already indicates that it is a view.
- Split your code into features modules: the structure will be much clearer and you will have the possibility to implement lazy-loading.
- Create one or several shared modules according to your needs, in order to group shared elements, and features used in several modules. For instance, you can create an AngularMaterialModule to store all imports and exports of all components from @angular/material. Another example would be a SharedModule to group reusable pieces of the application (lists, forms, generic dialogs...).
- Implement data-services specifically designed to interact with backend.
- Follow conventional naming: first the name of the functionality with dash if needed, then its type (feature.type.ts).
Conventional types are: .service, .component, .pipe, .module, et .directive.

Some examples :

- products-list.component.ts
- product.component.ts
- products.module.ts
- products-routing.module.ts
- products.service.ts

You should generate those files with the command 'ng generate [component/service/module...] [path]', it will do everything for you.

The decorator must match the file type, and the file must only contain one decorator. Do not mix several classes and interfaces in a single file. It would compromise readability and maintainability.

- Go for one solution between Template Driven Form and Reactive Form and use only one in the application to keep consistent.

- Configure project to avoid relative paths like `'../../../../'` in imports for .ts et .scss files.

`angular.json`
```
	(...)
    	"sourceRoot": "src",
	(...)
           "stylePreprocessorOptions": {
              "includePaths": [
                "src/app/styles",
              ]
            },
	(...)
```

## Performance

- Always unsubscribe from subscriptions. There are a few ways to do so, but you can for example set up an ObservableComponent to handle subscription destruction in a more generic way.

- Use trackBy in *ngFor loops to speed up rendering of big lists.

- Avoid too much logic in templates (see examples in [examples](#examples) part)

- Manually handle change detection if needed (ChangeDetectionStrategy OnPush)

- Don't create custom Pipes for a filtering or a sorting logic. These are expensive operations that you want to handle as few times as possible, for example in the component or in a service just before rendering the view.

- Be aware of animations that can impact the application fluidity.

- Keep an eye on external libraries that can have some functionalities with a strong impact on performance.

## Examples

- Example 1

Instead of:
```html
<p>Total guests : {{ total + 10 }}</p>
```

Go for:
```html
<p>Total : {{ totalGuests }}</p>
```

And then handle the operation in the controller (.ts file).

Option 1: add a property that you can update manually according to the component logic.

Option 2: use a getter

```ts
get totalGuests(): number {
	return this.total + 10;
}
```

- Example 2

```html
<h1>{{ getTitle() }}</h1>
```

Write this:

```html
<h1>{{ title }}</h1>
```

And update title in the controller when needed (maybe on the ngOnChanges lifecycle hook if it is an @Input, or on the ngOnInit if it never changes, or in some specific methods if necessary...). Doing so, we assure that the template rendering won't be slowed down by a function being executed all the time.

