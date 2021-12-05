---
layout: default
title: ECMAScript
permalink: /javascript/ecmascript/

---

# ECMAScript

Documentation sources :

[w3schools](https://www.w3schools.com/js/js_best_practices.asp)

# Best Practices

All the advices applied on Javascript can be transferred to other languages.

# Variable naming conventions

- All names start with a letter.
  The name must begin with a letter, a dollar sign \$ or an underscore \_. It must not begin with a number.
- We use camelCase for identifier names
  The name may contain letters, numbers, a dollar sign \$ or an underscore \_. You must not use a dash - or a period .
- In a variable name. You can't use keywords like var or new. You must also not give a name that is already used or will soon be used by Javascript.

## Declarations on Top

It is a good coding practice to put all declarations at the top of each script or function.

This will:

- Give cleaner code
- Provide a single place to look for local variables
- Make it easier to avoid unwanted (implied) global variables
- Reduce the possibility of unwanted re-declarations

## Short Functions, well-named and mono-task

The short functions are easy to read and contain. The name of the function should be sufficient to understand what it does. A function that does only one thing is easier to reuse, test and name. A function should not change its input parameters. It is preferable that it returns a new value and that's all it should do.

```javascript
// Pure function
function add(a, b) {
  return a + b;
}
// Not pure function
function add(a, b) {
  var x = a + b;
  console.log(x); // Doing other job than returning output
  return x;
}
```

## Modules and single responsibility

Divide code into small seperate modules where each module has a single functionality. A module will be easier to name, understand, test and reuse.

## Don't Use new keyword

- Use {} instead of new Object()
- Use "" instead of new String()
- Use 0 instead of new Number()
- Use false instead of new Boolean()
- Use [] instead of new Array()
- Use /()/ instead of new RegExp()
- Use function (){} instead of new Function()

```javascript
var x1 = {}; // new object
var x2 = ''; // new primitive string
var x3 = 0; // new primitive number
var x4 = false; // new primitive boolean
var x5 = []; // new array object
var x6 = /()/; // new regexp object
var x7 = function() {}; // new function object
```

## Use === Comparison

The == comparison operator always converts (to matching types) before comparison.

The === operator forces comparison of values and type:

```javascript
0 == ''; // true
1 == '1'; // true
1 == true; // true

0 === ''; // false
1 === '1'; // false
1 === true; // false
```

## Ask the right questions

#### (before New functionalities)

The development methodology is very important to avoid technical debt. The questions to ask before developing any new functionality are the following: The development process of a US or any new functionality is very important and must always follow the same steps.
All developers must follow the same path and ask themselves thr same questions:

- What components are needed to create this functionality?
- Do they already exist ?
- Do they need to be modified ?
- How will the component be accessible ?
- From the menu, through routing ?
- After a user action on another component ?
- In which folder should this component be stored ?
- Is it necessary to outsource it ?
- What inputs and outputs are required ?
- What are the backend routes necessary for its operation ?
- Do they already exist ?
- Do they need to be modified ?
- Is it necessary to create a form ?
- What are the necessary validations?
- Is it necessary to import an external library ?
- Is this or a similar library already used in the project ?

The development of the solution will be more serene when these issues have been addressed beforehand. The quality of the code is greatly affected.

## Structure the code

Shared modules. Try to create modules that can be used more than once in the code. This reduces code duplication and facilitates maintenance.

Use angular.json to build css files rather than importing files one by one into index.html.

Global or local CSS. When writing CSS code, ask yourself if this style could be used in other modules. If so, write this code at the application level rather than at the module level. This will avoid duplication of code. You can override this code at the module level if there is a need for a small specific modification in a module.

Use themes with SCSS. Create a file that contains all the variables for color, font, font size. This will help a lot with CSS maintenance and evolutions.

## Make comments

The code must be accompanied by comments to promote understanding of the treatments for future developers who will be involved in the project

## Use Unit Tests

To avoid regressions, the developer finishes his task by developing the unit test that will validate his code.

## Encouraging Factorisation

It is important to factor all or part of the code when a lack of control is noticed. This eliminates dead code and copy/paste code. A tidy code is much easier to improve. Do not hesitate to spend some time factoring your code before finishing your task.

## Managing Dependencies

Eliminate unnecessary or duplicate dependencies. Being careful to modify the code that depends on it.

## Outsource modules

Code factoring or analysis before creating new functionality can lead to the outsourcing of modules. Outsourcing functionalities allows the use of the same module in several applications or in several versions of the same application. It is important to export these modules in ES6 format.

## Lazy loading

Lazy loading is a design patter commonly used in computer programming to defer initialization of an object until the point as which is needed. Do not load the entire application when the first page loads. It is best to load items only when they are needed during the life cycle of the application.

## Implementing code reviews

All developers must deliver their code in a separate branch as a pull request. The lead dev has to review the code and approve it before it goes into the core. This ensures that every line of code has been proofread and helps correct errors that can't be detected by the linter.
