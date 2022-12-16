<div id="top"></div>

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h2 align="center">A Hobbit's Developer Style Guide</h2>

  <p align="center">
    A style guide for the layman developer. **In Development**
    <br />
    <a href="https://github.com/coltskeen/Style-Guide/issues">Report Bug</a>
    ·
    <a href="https://github.com/coltskeen/Style-Guide/issues">Request Feature</a>
  </p>
</div>

> ### "Arguments over style are pointless. There should be a style guide, and you should follow it"
> &emsp;_Rebecca_ _Murphey_

<!-- TABLE OF CONTENTS -->
<details>
  <summary id="table-of-contents">Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li><a href="#typescript-style-guide">TypeScript Style Guide</a></li>
      <ul>
        <li><a href="#variables">Variables</a></li>
        <li><a href="#classes-interfaces-types-and-namespaces">Classes, Interfaces, Types, and Namespaces</a></li>
        <li><a href="#enums">Enums</a></li>
      </ul>
    <li><a href="#angular-style-guide">Angular Style Guide</a></li>
    <li><a href="#c#-style-guide">C# Style Guide</a></li>
    <li><a href="#resources">Resources</a></li>
    <li><a href="#copyright">Copyright</a></li>
    <li><a href="#amendments">Amendments</a></li>
  </ol>
</details>



  1. [References](#references)
  1. [Objects](#objects)
  1. [Arrays](#arrays)
  1. [Destructuring](#destructuring)
  1. [Strings](#strings)
  1. [Functions](#functions)
  1. [Arrow Functions](#arrow-functions)
  1. [Classes & Constructors](#classes--constructors)
  1. [Modules](#modules)
  1. [Iterators and Generators](#iterators-and-generators)
  1. [Properties](#properties)
  1. [Hoisting](#hoisting)
  1. [Comparison Operators & Equality](#comparison-operators--equality)
  1. [Blocks](#blocks)
  1. [Control Statements](#control-statements)
  1. [Comments](#comments)
  1. [Whitespace](#whitespace)
  1. [Commas](#commas)
  1. [Semicolons](#semicolons)
  1. [Type Casting & Coercion](#type-casting--coercion)
  1. [Naming Conventions](#naming-conventions)
  1. [Accessors](#accessors)
  1. [Events](#events)
  1. [ECMAScript 5 Compatibility](#ecmascript-5-compatibility)
  1. [ECMAScript 6+ (ES 2015+) Styles](#ecmascript-6-es-2015-styles)
  1. [Standard Library](#standard-library)
  1. [Testing](#testing)
  1. [Performance](#performance)

  1. [Class](#class)
  1. [Interface](#interface)
  1. [Type](#type)
  1. [Namespace](#namespace)
  1. [Enum](#enum)
  1. [`null` vs. `undefined`](#null-vs-undefined)
  1. [Formatting](#formatting)
  1. [Single vs. Double Quotes](#quotes)
  1. [Tabs vs. Spaces](#spaces)
  1. [Use semicolons](#semicolons)
  1. [Annotate Arrays as `Type[]`](#array)
  1. [File Names](#filename)
  1. [`type` vs `interface`](#type-vs-interface)
  1. [`==` or `===`](#-or-)

<!-- ABOUT THE PROJECT -->
# About The Project

Ever find yourself scouring the multiple style guides and github repos to ensure your code is crafted with the expertise of wizard, only to get lost in the mass of detailed information that 80% of your layman work needs not to worry about? Well scour no more. This layman's style guide is the one to rule them all by bringing to you what you need most for your day-to-day adventures meandering through the highways and byways of Middle Earth (or in this case the inter-webs), easily searchable to make your magical code just right.


**[⬆ back to top](#table-of-contents)**

# TypeScript Style Guide

## Variables

  * **Rule:** Always use ```const``` or ```let``` to declare variables. Never use ```var```.
  * **Reason:** Using ```var``` will result in global variables. We want to avoid polluting the global namespace. Also ```const``` and ```let``` are block scoped, like variables in most other languages. ```var``` in TypeScript is function scoped, which can cause difficult to understand bugs. 

    ```ts
    // bad
    superPower = new SuperPower();

    // good
    const superPower = new SuperPower();
    ```

  * **Rule:** Use `camelCase` for variable and function names
  * **Reason:** Conventional TypeScript

    ```ts
    // bad
    var SuperPower;
    function SuperPowerFunc() { }

    // good
    var superPower;
    function superPowerFunc() { }
    ```

**[⬆ back to top](#table-of-contents)**

## Classes, Interfaces, Types, and Namespaces
* **Rule:** Use `PascalCase` for names but `camelCase` for members and methods
* **Reason:** This is fairly convential TypeScript.

  ```ts
  // bad
  class foo { }

  // good
  class Foo { }
  ```

  ```ts
  // bad
  class Foo {
      Bar: number;
      Baz() { }
  }

  // good
  class Foo {
      bar: number;
      baz() { }
  }
  ```

  ```ts
  // bad
  type user = {
    FirstName: string,
    LastName: string,
  }

  // good
  type User = {
    firstName: string,
    lastName: string,
  }

  ```

* **Rule:** **Don't** prefix interfaces with `I`
* **Reason:** Unconventional. `lib.d.ts` defines important interfaces without an `I` (e.g. Window, Document etc). Official TypeScript style defines interfaces without an `I`.

  ```ts
  // bad
  interface IFoo {
  }

  // good
  interface Foo {
  }
  ```

* **Rule:** Utilize the strongly typed nature of TypeScript wherever possible for functions, variables, and other data structures. Avoid the use of `any`.
* **Reason:** Our applications must be stable, reliable, scalable, and easily maintainable. Using types guards aids in catching bugs that otherwise would be missed, reducing support requirements. Annotated types also help to clarify written code for other developers.

  ```ts
  // bad
  let status;

  // bad
  let statusCode: any;

  // good
  let status: string;
  ```

  ```ts
  // bad
  function subtract(foo, bar) {
    return foo - bar;
  }

  // good
  function subtract(foo: number, bar: number): number {
    return foo - bar;
  }
  ```


**[⬆ back to top](#table-of-contents)**

## Enums
* **Rule:** Use `PascalCase` for names AND members
* **Reason:** This is convential TypeScript.

  ```ts
  // bad
  enum color {
    red
  }
  ```

  ```ts
  // good
  enum Color {
    Red
  }
  ```

**[⬆ back to top](#table-of-contents)**

# Angular Style Guide

# C# Style Guide

## Resources


**Read This**

  - [Standard ECMA-262](https://www.ecma-international.org/ecma-262/6.0/index.html)
  - [TypeScript Documentation](https://www.typescriptlang.org/docs/)
  - [C# Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/?WT.mc_id=dotnet-35129-website)

**Tools**

  - Code Style Linter - [ESlint](https://eslint.org/)
  - Partner Server-side Framework - [NestJs](https://docs.nestjs.com/)
  - Client-side Framework - [Angular](https://angular.io/docs)
  - Internal Server-side Frameworks
    - [Entity Framework Core](https://learn.microsoft.com/en-us/ef/core/)
    - [ASP.NET](https://learn.microsoft.com/en-us/aspnet/core/?WT.mc_id=dotnet-35129-website&view=aspnetcore-7.0)
  - Nest Testing
    - [Jest](https://jestjs.io/docs/getting-started)
  - Angular Testing
    - [Karma](https://angular.io/guide/testing)
    - [Jasmine](https://jasmine.github.io/pages/docs_home.html)

**Other Style Guides**

  - [Angular Style Guide](https://angular.io/guide/styleguide)
  - [Google Typescript Style Guide](https://google.github.io/styleguide/tsguide.html)
  - [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwaldron/idiomatic.js)

**Other Styles**

  - [Naming this in nested functions](https://gist.github.com/cjohansen/4135065) - Christian Johansen
  - [Conditional Callbacks](https://github.com/airbnb/javascript/issues/52) - Ross Allen

**Further Reading**

  - [ES6 Features](https://github.com/lukehoban/es6features) - Luke Hoban
  - [Frontend Guidelines](https://github.com/bendc/frontend-guidelines) - Benjamin De Cock

**Books**

  - [JavaScript: The Good Parts](https://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742) - Douglas Crockford
  - [JavaScript Patterns](https://www.amazon.com/JavaScript-Patterns-Stoyan-Stefanov/dp/0596806752) - Stoyan Stefanov
  - [Pro JavaScript Design Patterns](https://www.amazon.com/JavaScript-Design-Patterns-Recipes-Problem-Solution/dp/159059908X) - Ross Harmes and Dustin Diaz
  - [High Performance Web Sites: Essential Knowledge for Front-End Engineers](https://www.amazon.com/High-Performance-Web-Sites-Essential/dp/0596529309) - Steve Souders
  - [Maintainable JavaScript](https://www.amazon.com/Maintainable-JavaScript-Nicholas-C-Zakas/dp/1449327680) - Nicholas C. Zakas
  - [JavaScript Web Applications](https://www.amazon.com/JavaScript-Web-Applications-Alex-MacCaw/dp/144930351X) - Alex MacCaw
  - [Pro JavaScript Techniques](https://www.amazon.com/Pro-JavaScript-Techniques-John-Resig/dp/1590597273) - John Resig
  - [Smashing Node.js: JavaScript Everywhere](https://www.amazon.com/Smashing-Node-js-JavaScript-Everywhere-Magazine/dp/1119962595) - Guillermo Rauch
  - [Secrets of the JavaScript Ninja](https://www.amazon.com/Secrets-JavaScript-Ninja-John-Resig/dp/193398869X) - John Resig and Bear Bibeault
  - [Human JavaScript](http://humanjavascript.com/) - Henrik Joreteg
  - [Superhero.js](http://superherojs.com/) - Kim Joar Bekkelund, Mads Mobæk, & Olav Bjorkoy
  - [JSBooks](https://jsbooks.revolunet.com/) - Julien Bouquillon
  - [Third Party JavaScript](https://www.manning.com/books/third-party-javascript) - Ben Vinegar and Anton Kovalyov
  - [Effective JavaScript: 68 Specific Ways to Harness the Power of JavaScript](https://amzn.com/dp/0321812182) - David Herman
  - [Eloquent JavaScript](https://eloquentjavascript.net/) - Marijn Haverbeke
  - [You Don’t Know JS: ES6 & Beyond](https://shop.oreilly.com/product/0636920033769.do) - Kyle Simpson


**[⬆ back to top](#table-of-contents)**

## Copyright

Copyright (c) 2022 The Wizard

**[⬆ back to top](#table-of-contents)**

## Amendments

To propose changes to this style guide please follow the Gesa Development Team's standard submission procross via a pull request and peer review.

**[⬆ back to top](#table-of-contents)**