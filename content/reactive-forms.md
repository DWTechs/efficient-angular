---
layout: default
title: Reactive forms
permalink: /javascript/angular/reactive-forms/
---

Handling user input with forms is the cornerstone of many common applications. Applications use forms to enable users to log in, to update a profile, to enter sensitive information, and to perform many other data-entry tasks.

Reactive forms are forms where we define the structure of the form in the component class. i.e. we create the form model with **Form Groups**, **Form Controls**, and **FormArrays**. We also define the validation rules in the component class. Then, we bind it to the HTML form in the template. This is different from the template-driven forms, where we define the logic and controls in the HTML template.

To use reactive form controls, import **ReactiveFormsModule** from the *@angular/forms* package and add it to NgModule's imports array.

```typescript
import { ReactiveFormsModule } from '@angular/forms';

@NgModule({
  imports: [
    // other imports ...
    ReactiveFormsModule
  ],
})
export class AppModule { }
```

In Angular, form controls are classes that can hold both the data values and the validation information of any form element. Every form input we have in a reactive form should be bound by a **FormControl**. These are the basic units that make up reactive forms.

## Example

To see how this works, navigate to the user.component.ts file and paste in the code block below:
```typescript
import { Component, OnInit } from '@angular/core';
import { FormControl, FormGroup } from '@angular/forms'

@Component({
  selector: 'app-user',
  templateUrl: './user.component.html',
  styleUrls: ['./user.component.css']
})
export class UserComponent implements OnInit {
    infoSection = new FormGroup({
        name: new FormControl(''),
        email: new FormControl(''),
    });

    constructor() { }

    ngOnInit() {
    }

    onSubmit() { }
}
```
Here the form group was both imported and initialized to group together some form controls that compose the info section of the form. To reflect this group, we have to associate the model to the view with the form group name, like this:
```typescript
<form [formGroup]="infoSection" (ngSubmit)="onSubmit()">
   <label>
        Name:
        <input type="text" formControlName="name">
   </label>
    <label>
        Email:
        <input type="text" formControlName="email">
    </label>
    <button type="submit">Submit</button>
</form>
```

Validation