---
layout: default
title: CLI
permalink: /javascript/angular/cli/

---

## Angular CLI : Useful commands

### Create a feature module:

Execute the command:

```bash
ng generate module {module-name}
```

Shorter command:

```bash
ng g m {module-name}
```

For example, you can create an AuthenticationModule like this:
```bash
ng generate module authentication
```

To automatically create a routing module with your new module, you can add `--routing=true`:

```bash
ng g m {module-name} --routing=true
```

### Create a component

Execute the command:

```bash
ng generate component {module-directory-name}/{component-name}
```

Shorter command:

```bash
ng g c {module-directory-name}/{component-name}
```

For example, you can create a LoginComponent like this:

```bash
ng g c authentication/login
```

### Create a service

Execute the command:

```bash
ng generate service {module-directory-name}/services/{service-name}
```

Shorter command:

```bash
ng g s {module-directory-name}/services/{service-name}
```

For example, you can create an AuthenticationService like this:

```bash
ng g s authentication/services/authentication
```
