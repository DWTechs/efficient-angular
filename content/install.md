---
layout: default
title: Install
permalink: /javascript/angular/install/
---

# Start with Angular

## Set up environnement

### Nodejs install :

[https://nodejs.org/en/download/package-manager/](https://nodejs.org/en/download/package-manager/)

### Install / cli update :

[https://github.com/angular/angular-cli](https://github.com/angular/angular-cli)

## Generation of the Angular project

For generate projet with sass and standard routage, we need to execute this :

```bash
ng new dream-app-front --style=scss --routing --prefix=dream
```

## Arborescence presentation

### App folder Content

Content of folder is splite into three parts:

| Folder       | Description                                                |
| ------------ | ---------------------------------------------------------- |
| app/core/    | All services related to the core. (authentication, etc...) |
| app/features | Main features of the application.                          |
| app/ui/      | Common application components, pipes and guidelines        |

### App/ui folder content

This folder content element the reusable of the application

| Folder            | Description                                         |
| ----------------- | --------------------------------------------------- |
| app/ui/components | Components can be reused throughout the application |
| app/ui/directives | Guidelines can be reused throughout the application |
| app/ui/pipes      | Pipes reusable throughout the application           |

### App/features folder content

This folder content different fonctionality of the application

| Folder / Files                               | Description                                 |
| -------------------------------------------- | ------------------------------------------- |
| app/features/{name}>/components/             | Feature-specific components                 |
| app/features/{name}>/pages/                  | Contains the different pages of the feature |
| app/features/{name}>/shared/                 | Shared services and models in the feature   |
| app/features/{name}/{name}-routing.module.ts | Angular feature routing file                |
| app/features/{name}/{name}.module.ts         | Module Angular of the feature               |

```
app/
|- app.module.ts
|- app-routing.module.ts
|- core/
    |- auth/
        |- auth.service.ts
        |- index.ts
    |- othermoduleofglobalservice/
|- features/
    |- cars/
        |- cars.module.ts
        |- cars-routing.module.ts
        |- components/
            |- car-form/
                |- car-details.component.html
                |- car-details.component.scss
                |- car-details.component.spec.ts
                |- car-details.component.ts
            |- cars-list/
                |- cars-list.component.html
                |- cars-list.component.scss
                |- cars-list.component.spec.ts
                |- cars-list.component.ts
        |- pages/
            |- car-edit/
                |- car-edit.component.html
                |- car-edit.component.scss
                |- car-edit.component.spec.ts
                |- car-edit.component.ts
            |- cars/
                |- cars.component.html
                |- cars.component.scss
                |- cars.component.spec.ts
                |- cars.component.ts
        |- shared/
            |- cars.service.spec.ts
            |- cars.service.ts
            |- car.model.ts

    |- othermoduleofpages/
|- ui/
    |- components/
        |- nav-bar
            |- nav-bar.module.ts
            |- index.ts
            |- nav-bar/
                |- nav-bar.component.html
                |- nav-bar.component.scss
                |- nav-bar.component.spec.ts
                |- nav-bar.component.ts
    |- directives
    |- pipes
```

## Shared Folders

Shared folder pattern

|- Shared
|- enums
|- models
|- representations
|- services

All files in these folders must be prefixed by the name of the feature.
Exemple : Caddy-comand-type-enum.ts

| Folder          | Description                                                                                                              |
| --------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Enums           | enums of feature                                                                                                         |
| Models          | the models of the feature, for example a model for a form,... (component specific)                                       |
| Représentations | the models from the backend (they are prefixed by representation at the end)                                             |
| Services        | we find the business services and web-services. For each microservice, there is a folder with a web-service file inside. |

## Librairy essentials

- [ng-bootstrap ](https://ng-bootstrap.github.io/#/getting-started)
<l>
