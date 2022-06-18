---
layout: default
title: CLI
permalink: /javascript/angular/cli/

---

## Angular CLI : Scaffold generation

### Create a feature module:

Execute the command:

```bash
ng generate module features/{feature-name} --module="app.module.ts" --routing
```

### Create a page of feature

Executer la commande :

```bash
ng generate component features/{feature-name}/pages/{page-name}
```

### Create a component of feature

Executer la commande :

```bash
ng generate component features/{feature-name}/components/{component-name}
```

### Create a service of feature

Executer la commande :

```bash
ng generate service features/{feature-name}/shared/{service-name}
```

### Create a model of feature

Executer la commande :

```bash
ng generate class features/{feature-name}/shared/{model-name} --type=model
```
