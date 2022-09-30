---
layout: default
title: Modules
permalink: /javascript/angular/modules/
---

NgModules are a great way to organize an application and keep code related to a specific functionality or feature separate from other code. Use NgModules to consolidate components, directives, and pipes into cohesive blocks of functionality.

Modules are a great way to organize an application and extend it with capabilities from external libraries. 

An NgModule is a class marked by the **@NgModule** decorator. **@NgModule** takes a metadata object that describes how to compile a component's template and how to create an injector at runtime. It identifies the module's own components, directives, and pipes, making some of them public, through the **exports** property, so that external components can use them.  **@NgModule** can also add service providers to the application dependency injectors.

## How to Create NgModules?
1. Firstly , we will import ‘NgModules’ from ‘@angular/core’.
2. Once imported, the decorator can be used to declare all the components and services used by that particular module.
3. And finally, we will be export the module using ‘export’ keyword which can be used by other modules.
```typescript
import { NgModule } from "@angular/core";

@NgModule({

    ...

})

export class AppModule{}
```

## Metadata of NgModules:
Now we will see the various properties that are available while creating an NgModule. There are five main properties as listed below:

- Declarations
- Exports
- Imports
- Bootstrap
- Providers

### Declarations
The first property is called a declaration, where we will declare all the components, directives, and pipes which are available to a particular feature.

```typescript
    declarations : [
        Components,
        Directives,
        Pipes
    ]
```
### Exports
When module A is imported by module B, then we have to export the module A in order to be used by other modules. By exporting module A, we can use any of the components, directives, services or pipes present in module A in any imported module.

This is based on the object oriented programming concept, where the components, directives, and pipes are by default private and we need to add them in the export module to make it usable by other modules.

```typescript
    exports : [
        PublicComponents,
        PublicDirectives,
        PublicPipes
    ]
```
### Imports
All the exported components and pipes from other modules can be imported in a module by declaring them in an import section of NgModule.
```typescript
    imports : [
        ModuleA,
        ModuleB,
        ModuleC
        ]
```
### Bootstrap
In the bootstrap property the root component will be declared which is used to initially load our application by calling the component declared here. Usually, the App Component is the default component that will be declared here in any Angular application.

```typescript
    bootstrap : [
        RootComponent
    ]
```
### Providers
In the providers property, we provide all the data providers like services and auth guards here. So these services can be used in the declared module and all the modules which import this particular module.

```typescript
    providers : [
        Services,
        Guards
    ]
```

## Types of Angular Modules
Angular contains one root module as a necessary module for an application to work. Whereas there are also feature modules that you can create and define. You can have only one root module, but you can have multiple feature modules depending upon the requirements of your application.

The basic visible difference between the root module and other feature modules is that the *root module* imports **BrowserModule** whereas the *feature module* imports **CommonModule**. This difference is visible in the import property of the NgModule decorator.
