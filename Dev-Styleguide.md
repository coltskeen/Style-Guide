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
        <li><a href="#naming-conventions">Naming Conventions</a></li>
        <li><a href="#comments">Comments</a></li>
        <li><a href="#variables">Variables</a></li>
        <li><a href="#constants">Constants</a></li>
        <li><a href="#classes-interfaces-types-and-namespaces">Classes, Interfaces, Types, and Namespaces</a></li>
        <li><a href="#enums">Enums</a></li>
        <li><a href="#semicolons">Semicolons</a></li>
        <li><a href="#whitespace">Whitespace</a></li>
      </ul>
    <li><a href="#angular-style-guide">Angular Style Guide</a></li>
    <li><a href="#c#-style-guide">C# Style Guide</a></li>
    <li><a href="#resources">Resources</a></li>
    <li><a href="#copyright">Copyright</a></li>
    <li><a href="#amendments">Amendments</a></li>
  </ol>
</details>




  1. [Destructuring](#destructuring)




<!-- ABOUT THE PROJECT -->
# About The Project

Ever find yourself scouring the multiple style guides and github repos to ensure your code is crafted with the expertise of wizard, only to get lost in the mass of detailed information that 80% of your layman work needs not to worry about? Well scour no more. This layman's style guide is the one to rule them all by bringing to you what you need most for your day-to-day adventures meandering through the highways and byways of Middle Earth (or in this case the inter-webs), easily searchable to make your magical code just right.


**[⬆ back to top](#table-of-contents)**

# TypeScript Style Guide


## Naming Conventions

  * **Rule:** Names _must_ be descriptive and clear to a new reader. Do not use abbreviations that are ambiguous or unfamiliar to readers outside your project. 
  * **Reason:** Ensure code readability and reduces time needed for explanation and/or familiarization.

    ```ts
    // bad
    const supPwr = new SuperPower();

    // good
    const superPower = new SuperPower();
    ```

  * **Rule:** Names that are too long can decrease readability. So omit irrelevant details, words that are obvious from the type declaration, and words that are clear from the context.
  * **Reason:** TypeScript expresses information in types, so names _should not_ be decorate with information that is included in the type.

    ```ts
    // bad - too specific
    Monster finalBattleMostDangerousBossMonster; 
    Payments nonTypicalMonthlyPayments;

    // good 
    Monster boss; 
    Payments payments;

    
    // bad - the type tells us what these variables are:
    String nameString; 
    List<datetime> holidayDateList;

    // good
    String name; 
    List<datetime> holidays;

    
    // bad - repeating the context:
    class AnnualHolidaySale {int annualSaleRebate; boolean promoteHolidaySale() {...}}

    // good
    class AnnualHolidaySale {int rebate; boolean promote() {...}}
    ```

**[⬆ back to top](#table-of-contents)**

## Comments

  * **Rule:** Use `/** JSDoc */` comments for documentation and multi-line comments, i.e. comments a user of the code should read.
  * **Rule:** Use `// line comments` for implementation comments and single-line comments, i.e. comments that only concern the implementation of the code itself.
  * **Reason:** JSDoc comments are understood by tools (such as editors and documentation generators), while ordinary comments are only for other humans.

    ```ts
    /**
     * Multiple lines of JSDoc text are written here,
     * wrapped normally.
     * @param {number} arg A number to do something to.
     */
     function doSomething(arg) { … }
    ```

  * **Rule:** Start all comments with a space.
  * **Reason:** It's easier to read.

    ```ts
    //bad
    const boolean = true;

    // good
    const boolean = true;
    ```

  * **Rule:** Use `// FIXME:` to annotate problems that need to be figured out and `// TODO:` to annotate solutions to problems that need to be implemented.
  * **Reason:** Help other developers quickly understand whether you're pointing out a problem that needs to be revisited or suggesting a solution that needs implementing.

    ```ts
    class Calculator extends Abacus {
      constructor() {
        super();

        // FIXME: shouldn’t use a global here
        total = 0;

        // TODO: sum should be configurable by an options param
        this.sum = 0;
      }
    }
    ```

**[⬆ back to top](#table-of-contents)**

## Variables

  * **Rule:** Always use ```const``` or ```let``` to declare variables. Never use ```var```.
  * **Reason:** Using ```var``` will result in global variables. We want to avoid polluting the global namespace. Also ```const``` and ```let``` are block scoped, like variables in most other languages. ```var``` in TypeScript is function scoped, which can cause difficult to understand bugs. 

    ```ts
    // bad
    const superPower = new SuperPower();

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

## Constants

* **Rule:** Write constants in CONSTANT_CASE
* **Reason:** Constant case is used when a value is intended to not be changed. Note that you can also include `static readonly` property in a class.

  ```ts
  // bad
  const unitTypes = {
    'days' = 'd',
    'months' = 'm',
    'years' = 'y'
  }

  // good
  const UNIT_TYPES = {
    'days' = 'd',
    'months' = 'm',
    'years' = 'y'
  }

  // good
  class Foo {
    private static readonly MY_SPECIAL_NUMBER = 5;

    bar() {
      return 2 * Foo.MY_SPECIAL_NUMBER;
    }
  }
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
 
  // good
  enum Color {
    Red
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Semicolons

* **Rule:** Do not use Automatic Semicolon Insertion (ASI). Always explicit terminate statements with a semicolon.
* **Reason:** This prevents bugs.

  ```ts
  // bad
  const foo: Foo = await service.Create()
 
  // good
  const foo: Foo = await service.Create();
  ```

**[⬆ back to top](#table-of-contents)**

## Whitespace

  * **Rule:** Place 1 space before the opening parenthesis in control statements (if, while etc.) but no space between the argument list and the function name in function calls and declarations.
  * **Reason:** Readability and consistency.

    ```ts
    // bad
    if(isJedi) {
      fight ();
    }

    // good
    if (isJedi) {
      fight();
    }

    // bad
    function fight () {
      console.log ('Swooosh!');
    }

    // good
    function fight() {
      console.log('Swooosh!');
    }
    ```

  * **Rule:** Set off operators with spaces.
  * **Reason:** Readability and consistency.

    ```ts
    // bad
    const x=y+5;

    // good
    const x = y + 5;
    ```


  * **Rule:** Add spaces inside curly braces but not parenthesis or brackets.
  * **Reason:** Readability and consistency.

    ```ts
    // bad
    if ( foo ) { }
    const foo = [ 1, 2, 3 ]
    const foo = {clark: 'kent'};

    // good
    if (foo) { }
    const foo = [1, 2, 3]
    const foo = { clark: 'kent' };
    ```

  * **Rule:**  Avoid having lines of code that are longer than 100 characters (including whitespace). 
  * **Reason:** This ensures readability and maintainability.

    ```ts
    // bad
    const foo = jsonData && jsonData.foo && jsonData.foo.bar && jsonData.foo.bar.baz && jsonData.foo.bar.baz.quux && jsonData.foo.bar.baz.quux.xyzzy;

    // good
    const foo = jsonData
      && jsonData.foo
      && jsonData.foo.bar
      && jsonData.foo.bar.baz
      && jsonData.foo.bar.baz.quux
      && jsonData.foo.bar.baz.quux.xyzzy;

    // even better
    const foo = jsonData
      ?.foo
      ?.bar
      ?.baz
      ?.quux
      ?.xyzzy;
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

  - [Advanced TypeScript Programming Projects](https://www.amazon.com/Advanced-TypeScript-Programming-Projects-JavaScript-ebook/dp/B07R8MB288) - Peter O'Hanlon
  - [Effective TypeScript](https://effectivetypescript.com/) - Dan Vanderkam
  - [Essential TypeScript 4](https://www.amazon.com/Essential-TypeScript-4-Beginner-Pro/dp/148427010X) - Adam Freeman
  - [Eloquent JavaScript](https://eloquentjavascript.net/) - Marijn Haverbeke


**[⬆ back to top](#table-of-contents)**

## Copyright

Copyright (c) 2022 The Wizard

**[⬆ back to top](#table-of-contents)**

## Amendments

To propose changes to this style guide please follow the Gesa Development Team's standard submission procross via a pull request and peer review.

**[⬆ back to top](#table-of-contents)**