<div id="top"></div>

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="assets/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h2 align="center">A Hobbit's Developer Style Guide</h2>

  <p align="center">
    A style guide for the layman developer. You want the spark notes? You got it!
    <br />
    <a href="https://github.com/coltskeen/Style-Guide">Style Guide Overview</a>
    ·
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
    <li><a href="#about-the-project">About The Project</a></li>
    <li><a href="#note-on-consistency">Note on Consistency</a></li>
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
        <li><a href="#exceptions">Exceptions</a></li>
        <li><a href="#iterating-objects">Iterating objects</a></li>
      </ul>
    <li><a href="#angular-style-guide">Angular Style Guide</a></li>
      <ul>
        <li><a href="#single-responsibility-principle">Single Responsibility Principle</a></li>
        <li><a href="#angular-naming-conventions">Angular Naming Conventions</a></li>
        <li><a href="#application-structure">Application Structure</a></li>
        <li><a href="#components">Components</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#lifecycle-hooks">Lifecycle Hooks</a></li>
      </ul>
    <li><a href="#c♯-style-guide">C♯ Style Guide</a></li>
      <ul>
        <li><a href="#c♯-naming-conventions">C♯ Naming Conventions</a></li>
        <li><a href="#layout-conventions">Layout Conventions</a></li>
        <li><a href="#commenting-conventions">Commenting Conventions</a></li>
        <li><a href="#language-guidelines">Language Guidelines</a></li>
          <ul>
            <li><a href="#implicit-types">Implicit Types</a></li>
            <li><a href="#exception-handling-syntax">Exception Handling Syntax</a></li>
            <li><a href="#operators">&&, ||, and new Operators</a></li>
            <li><a href="#linq-queries">LINQ Queries</a></li>
            <li><a href="#dotnet-coding-style">Dotnet Coding Style</a></li>
            <li><a href="#array-vs-list">Array vs List</a></li>
          </ul>
      </ul>
    <li><a href="#resources">Resources</a></li>
    <li><a href="#copyright">Copyright</a></li>
    <li><a href="#amendments">Amendments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
# About The Project

Ever find yourself scouring the multiple style guides and github repos to ensure your code is crafted with the expertise of wizard, only to get lost in the mass of detailed information that 80% of your layman work needs not to worry about? Well scour no more. This layman's style guide is the one to rule them all by bringing to you what you need most for your day-to-day adventures meandering through the highways and byways of Middle Earth (or in this case the inter-webs), easily searchable to make your magical code just right.

# Note on Consistency

For any style question that isn't settled definitively by this styleguide, do what the other code in the same file is already doing (be consistent). If that doesn't resolve the question, consider emulating the other files in the same directory. At all times, remember that code reviewers should not focus on simply enforcing the rules in this styleguide, but instead focus on improving overall code quality.


**[⬆ back to top](#table-of-contents)**

# TypeScript Style Guide

The information in this section is derived from the official [Google TypeScript Guide](https://google.github.io/styleguide/tsguide.html), the [AirBnb style guide](https://github.com/airbnb/javascript), and the [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/styleguide) styleguide. This guide contains highlights of the common rules and patterns that a developer should consider following - or have a really good reason as to why they are breaking from the norm. 

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
    Monster finalBoss; 
    Payments nonTypicalPayments;

    
    // bad - the type tells us what these variables are:
    String nameString; 
    Array<datetime> holidayDateList;

    // good
    String name; 
    Array<datetime> holidays;

    
    // bad - repeating the context:
    class AnnualHolidaySale {int annualSaleRebate; boolean promoteHolidaySale() {...}}

    // good
    class AnnualHolidaySale {int rebate; boolean promote() {...}}
    ```

**[⬆ back to top](#table-of-contents)**

## Comments

  * **Rules:** 
      * Use `/** JSDoc */` comments for documentation and multi-line comments, i.e. comments a user of the code should read.
      * Use `// line comments` for implementation comments and single-line comments, i.e. comments that only concern the implementation of the code itself.
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

  * **Rules:**
      * Place the comment on a separate line, not at the end of a line of code.
      * Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.
  * **Reason:** Consistency and yes... even readability!

    ```ts
    // The following declaration creates a query.
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

  * **Rule:** Do not use namespaces unless required to interface with external, third party code. In all other cases, use modules with imports and exports.
  * **Reason:** Namespaces are disallowed.

    ```ts
    // bad
    namespace MySpace {
      function getSocial() {}
    } 
    ```

  * **Rule:** By default annotate types on variables, classes, etc. However, sometimes using the `any` type is legitmate. In such cases, add a comment that suppresses the lint warning, and document why it is legitimate.
  * **Reason:** For quick understanding by other devs and for maintainability purposes.

    ```ts
    // This is an intentionally unsafe partial mock becuase ...
    // tslint:disable-next-line:no-any
    const mockBookService = ({get() { return mockBook; }} as any) as BookService;
    // Shopping cart is not used in this test
    // tslint:disable-next-line:no-any
    const component = new MyComponent(mockBookService, /* unused ShoppingCart */ null as any);
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

## Exceptions

  * **Rule:** Always use `new Error()` instead of `Error()` or throwing arbitrary values when instantiating expections.
  * **Reason:** More consistent with how objects are instantiated.

    ```ts
    // bad - does not get a stack trace filled in
    throw 'error message';

    // bad 
    throw Error('error message');

    // good
    throw new Error('error message');
    ```

**[⬆ back to top](#table-of-contents)**

## Iterating objects

  * **Rule:** Do not iterate over objects or arrays with `for (... in ... )`. Use `for (... of ...)`, `forEach`, or regular `for` loops.
  * **Reason:** It's error prone and can include enumerable properties from the prototype chain or give the array indices as strings instead of values.

    ```ts
    // bad - x could come from some parent prototype!
    for (const x in someObj) { }

    // bad 
    for (const x in someArray) { }

    // good
    for (const x of Object.keys(someObj)) { }

    // good
    for (let i = 0; i < someArr.length; i++) { }
    ```

**[⬆ back to top](#table-of-contents)**


## Imports and Exports

  * **Rule:** Do not use `require` for imports.
  * **Reason:** It's the old syntax. Use ES6 module syntax.

    ```ts
    // bad 
    const x = require('myDep');

    // good
    import x from './myDep';
    ```

  * **Rule:** Use named exports in all code.
  * **Reason:** Ensures all imports follow a uniform pattern and helps woth central maintenance.

    ```ts
    // bad 
    export default class MyClass { }

    // good
    export class MyClass { }
    ```

**[⬆ back to top](#table-of-contents)**

# Angular Style Guide

This section is derived from the official [Angular Style Guide](https://angular.io/guide/styleguide). It contains highlights that Angular developers should consider following - unless you have a significant reason to deviate. Again this is not comprehensive of all rules recommended in the official style guide but the spark notes version. 

## Single Responsibility Principle

  * **Rule:** Define one thing, such as a service or component, per file, and consider limiting files to 300 lines of code.
  * **Reason:** Avoids bugs and makes code easier to read and maintain.

    ```ts
    // bad - the model should be separated to its own file
    import { Component, OnInit } from '@angular/core';

    interface Hero {
      id: number;
      name: string;
    }

    @Component({
      selector: 'app-root',
      templateUrl: './hero-button.component.html'
      styleUrls: ['app/app.component.css']
    })
    class AppComponent implements OnInit {
      title = 'Tour of Heroes';

      heroes: Hero[] = [];

      ngOnInit() {
        getHeroes().then(heroes => (this.heroes = heroes));
      }
    }
    ```

  * **Rule:** Keep functions small. Consider limiting them to no more than 30 lines.
  * **Reason:** Avoids bugs and makes code easier to read and maintain.

**[⬆ back to top](#table-of-contents)**

## Angular Naming Conventions

  * **Rules:** 
      * Be consistent with file names. Use the angular recommended pattern `feature.type.ts`.
      * Use dashes and dots to separate names. Don't abbreviate the types.
  * **Reason:** Increases team efficiency by making files clear and easier to find.

    ```ts
    // bad
    heroList.component.ts
    hero-list.comp.ts

    // good
    hero-list.component.ts
    ```

  * **Rule:** Class names should be upper camel case and match the name of the file.
  * **Reason:** Consistent conventions make it easy to quickly identify and reference assets of different types.

    ```ts
    @Component({ … }) 
    export class HeroListComponent { } // Filename matches -> hero-list.component.ts
    ```

  * **Rule:** Do use _dashed-case_ for naming the element selectors of components.
  * **Reason:** Keeps the element names consistent with the specification for custom elements.

    ```ts
    // bad
    @Component({
      selector: 'tohHeroButton',
      templateUrl: './hero-button.component.html'
    })
    export class HeroButtonComponent {}

    // good
    @Component({
      selector: 'toh-hero-button',
      templateUrl: './hero-button.component.html'
    })
    export class HeroButtonComponent {}
    ```

  * **Rule:** Do use lower camel case for directives selectors.
  * **Reason:** The Angular HTML parser is case-sensitive and recognizes lower camel case.

    ```ts
    // good
    @Directive({
      selector: '[tohValidate]'
    })
    export class ValidateDirective {}
    ```

  * **Rule:** Unit test file names should be the same as the component they test but with the `.spec` suffix.
  * **Reason:** Provides pattern matching for `karma` or other test runners.

    ```ts
    // good
    hero-list.component.spec.ts
    ```



## Application Structure

  * **Rules:** 
      * Put all the application's code in the `src` folder but separate out all feature areas within this folder with their own NgModule.
      * All third party scripts should be stored in another folder (not the `src` folder).
      * Follow the LIFT principles. Structure the application such that you can **L**ocate code quickly, **I**dentify the code at a glance, keep the **F**lattest structure you can, and **T**ry to be DRY
      * Create folders by the feature area they represent such as `hero` or `villian`.
      * Create NgModules for the root module, each feature module, and the shared module. 
  * **Reason:** Consistency and avoiding clutter in your codebase as you scale the project.

_Figure 1: Example Folder Stucture:_

  ![Compliant Folder Structure Example](./images/AngularFolderStructure.PNG)


**[⬆ back to top](#table-of-contents)**

## Components

  * **Rule:** Give components an _element_ selector instead an attribute or class selector.
  * **Reason:** Easier to recognize that it is a component in the template's html.

    ```ts
    // bad
    <div tohHeroButton></div>

    // good 
    <toh-hero-button></toh-hero-button>
    ```

  * **Rule:** Always extract templates and styles into a separate file.
  * **Reason:** Large, inline templates and styles obscure the component's purpose and implementation, reducing readability and maintainability.

    ```ts
    // bad
    @Component({
      selector: 'toh-heroes',
      template: `
        <div>
          <h2>My Heroes</h2>
          <ul class="heroes">
            <li *ngFor="let hero of heroes | async" (click)="selectedHero=hero">
              <span class="badge">{{hero.id}}</span> {{hero.name}}
            </li>
          </ul>
          <div *ngIf="selectedHero">
            <h2>{{selectedHero.name | uppercase}} is my hero</h2>
          </div>
        </div>
      `,
      styles: [`
        .heroes { ... }
        .heroes li { ... }
        .heroes .badge { ... }
      `]
    })
    export class HeroesComponent {
      heroes: Observable<Hero[]>;
      selectedHero!: Hero;

      constructor(private heroService: HeroService) {
        this.heroes = this.heroService.getHeroes();
      }
    }

    // good
    @Component({
      selector: 'toh-heroes',
      templateUrl: './heroes.component.html',
      styleUrls:  ['./heroes.component.css']
    })
    export class HeroesComponent {
      heroes: Observable<Hero[]>;
      selectedHero!: Hero;

      constructor(private heroService: HeroService) {
        this.heroes = this.heroService.getHeroes();
      }
    }
    ```

**[⬆ back to top](#table-of-contents)**

  * **Rule:** Place properties up top in the file, followed by methods. Private members go after the public members.
  * **Reason:** Consistency in the sequence helps with readability.

    ```ts
    // bad
    export class ToastComponent implements OnInit {
      // properties and fields mixed up
      private defaults = { ... };
      message: string;
      title: string;
      private toastElement: any;

      // public and private methods mixed up
      ngOnInit() { ... }
      private hide() { ... }
      activate(message = this.defaults.message, title = this.defaults.title) { ... }
      private show() { ... }
    }

    // good
    export class ToastComponent implements OnInit {
      // public properties
      message = '';
      title = '';

      // private fields
      private defaults = { ... };
      private toastElement: any;

      // public methods
      activate(message = this.defaults.message, title = this.defaults.title) { ... }
      ngOnInit() { ...  }

      // private methods
      private hide() { ... }
      private show() { ... }
    }
    ```

  * **Rules:** 
      * Limit logic in a component to only that required for the view. All other logic should be delegated to services. 
      * Move reusable logic to services and keep components simple and focused on their intended purpose.
  * **Reason:** More easily reusable logic that can be more easily isolated for unit testing.

    ```ts
    // bad
    export class HeroListComponent implements OnInit {
      heroes: Hero[];
      constructor(private http: HttpClient) {}
      getHeroes() {
        this.heroes = [];
        this.http.get(heroesUrl).pipe(
          catchError(this.catchBadResponse),
          finalize(() => this.hideSpinner())
        ).subscribe((heroes: Hero[]) => this.heroes = heroes);
      }
      ngOnInit() {
        this.getHeroes();
      }

      private catchBadResponse(err: any, source: Observable<any>) { ... }
      private hideSpinner() { ... }
    }
    
    // good
    import { Component, OnInit } from '@angular/core';
    // put logic in the service and import it
    import { Hero, HeroService } from '../shared';

    @Component({ ... })
    export class HeroListComponent implements OnInit {
      heroes: Hero[] = [];
      constructor(private heroService: HeroService) {}
      getHeroes() {
        this.heroes = [];
        this.heroService.getHeroes()
          .subscribe(heroes => this.heroes = heroes);
      }
      ngOnInit() {
        this.getHeroes();
      }
    }
    ```

**[⬆ back to top](#table-of-contents)**

## Services

  * **Rules:** 
      * Use services as singletons within the same injector. Use them for sharing data and functionality.
      * Maintain single responsibility encapsulated by context in services.
      * Provide services in the root injector in the `@Injectable` decorator of the service
  * **Reason:** Services are ideal for sharing methods, instances, and stateful in-memory data.

**[⬆ back to top](#table-of-contents)**

## Lifecycle Hooks

  * **Rule:** Implement lifecycle hooks interfaces.
  * **Reason:** It helps with flagging misspellings or syntax errors.

    ```ts
    // bad
    export class HeroButtonComponent {
      onInit() { // misspelled
        console.log('The component is initialized');
      }
    }

    // good
    export class HeroButtonComponent implements OnInit {
      ngOnInit() {
        console.log('The component is initialized');
      }
    }
    ```

**[⬆ back to top](#table-of-contents)**

# C♯ Style Guide

This section is derived from the official [Microsoft C# Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/). It contains highlights that C# developers should consider following - unless you have a significant reason to deviate. Again this is not comprehensive of all rules recommended in the official documentation but the spark notes version. 

  * **#1 Rule:** Use Visual Studio Defaults!"

## C♯ Naming Conventions

  * **Rule:** Use `PascalCase` when naming a `class`, `record`, or `struct`.
  * **Reason:** Consistency and readability.

    ```c#
    // bad
    public class myClass
    {
    }

    // good
    public class MyClass
    {
    }
    ```

  * **Rule:** Prefix `interfaces` with and `I`.
  * **Reason:** Clearing indicates to the developer it's an interface.

    ```c#
    // bad
    public interface MyInterface
    {
    }

    // good
    public interface IMyInterface
    {
    }
    ```

  * **Rule:** Public members of types should use `PascalCase`.
  * **Reason:** Consistency and readability.

    ```c#
    // bad
    public class Example
    {
        // A public field, these should be used sparingly
        public bool isValid;

        // An init-only property
        public IWorkerQueue workerQueue { get; init; }

        // An event
        public event Action eventProcessing;

        // Method
        public void startEventProcessing()
        { ... }
    }

    // good
    public class Example
    {
        // A public field, these should be used sparingly
        public bool IsValid;

        // An init-only property
        public IWorkerQueue WorkerQueue { get; init; }

        // An event
        public event Action EventProcessing;

        // Method
        public void StartEventProcessing()
        { ... }
    }
    ```

  * **Rules:** 
      * Use `camelCase` for `private` or `internal` fields and prefix them with and underscore `_`.
      * When working with `static` fields that are `private` or `internal`, use the `s_` prefix and for thread static use `t_`.
  * **Reason:** Consistency and readability.

    ```c#
    // bad
    public class MyBeeService
    {
      private IWorkerBee WorkerBee;
    }

    // good
    public class MyBeeService
    {
      private IWorkerBee _workerBee;
    }

    // bad
    public class MyBeeService
    {
      // static fields need the s_
      private static IWorkerBee _workerBee
      // thread static requires t_
      [ThreadStatic]
      private static TimeSpan _timeSpan;
    }

    // good
    public class MyBeeService
    {
      // static fields need the s_
      private static IWorkerBee s_workerBee
      // thread static requires t_
      [ThreadStatic]
      private static TimeSpan t_timeSpan;
    }
    ```


**[⬆ back to top](#table-of-contents)**

## Layout Conventions

  * **Rules:** 
      * When in doubt use the default Code Editor settings.
      * Write only one statement or declaration per line.
      * If continuation lines are not indented automatically, indent them one tab stop (four spaces).
      * Add at least one blank line between method definitions and property definitions.
      * Use parentheses to make clauses in an expression apparent, as shown in the following code.
  * **Reason:** Microsoft C# convention

    ```c#
    if ((val1 > val2) && (val1 > val3))
    {
        // Take appropriate action.
    }
    ```


**[⬆ back to top](#table-of-contents)**

## Commenting Conventions

  * **Rules:** 
      * Use `/** JSDoc */` comments for documentation and multi-line comments, i.e. comments a user of the code should read.
      * Use `// line comments` for implementation comments and single-line comments, i.e. comments that only concern the implementation of the code itself.
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

  * **Rules:**
      * Place the comment on a separate line, not at the end of a line of code.
      * Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.
  * **Reason:** Consistency and yes... even readability!

    ```c#
    // The following declaration creates a query.
    ```

**[⬆ back to top](#table-of-contents)**

## Language Guidelines

### Implicit Types

  * **Rules:** 
      * Use implicit typing for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.
      * Don't use `var` when the type is not apparent from the right side of the assignment. A variable type is considered clear if it's a new operator or an explicit cast.
      * Don't rely on the variable name to specify the type of the variable. It might not be correct and can be misleading.
      * Use implicit typing in `for` loops but not `foreach` loops. 
  * **Reason:** Avoiding unecessary code and code clarity.

    ```c#
    // unnecessary
    string var = "This is clearly a string.";
    int var = 27;

    // good
    var var1 = "This is clearly a string.";
    var var2 = 27;

    // bad - not a new operator or explicit cast
    var var3 = Convert.ToInt32(Console.ReadLine()); 
    var var4 = ExampleClass.ResultSoFar();

    // good
    int var3 = Convert.ToInt32(Console.ReadLine()); 
    int var4 = ExampleClass.ResultSoFar();

    // bad - misleading
    var inputInt = Console.ReadLine();

    // good
    string input = Console.ReadLine();

    // bad - unecessary
    for (int i = 0; i < 10000; i++)
    { ... }

    // good
    for (var i = 0; i < 10000; i++)
    { ... }

    // bad - type isn't obvious for implicit typing
    foreach (var ch in laugh)
    { ... }

    // good
    foreach (char ch in laugh)
    { ... }
    ```

**[⬆ back to top](#table-of-contents)**

### Exception Handling Syntax


  * **Rule:** Use a try-catch statement for most exception handling.
  * **Reason:** C# Convention! Ensures consistency.

    ```c#
    // good
    static string GetValueFromArray(string[] array, int index)
    {
        try
        {
            return array[index];
        }
        catch (System.IndexOutOfRangeException ex)
        {
            Console.WriteLine("Index is out of range: {0}", index);
            throw;
        }
    }
    ```

  * **Rule:** Simplify your code by using the C# `using` statement. If you have a `try`-`finally` statement in which the only code in the `finally` block is a call to the `Dispose` method, use a using statement instead.
  * **Reason:** Code simplicity helps with code readability.

    ```c#
    // good
    Font font1 = new Font("Arial", 10.0f);
    try
    {
        byte charset = font1.GdiCharSet;
    }
    finally
    {
        if (font1 != null)
        {
            ((IDisposable)font1).Dispose();
        }
    }

    // better
    using (Font font2 = new Font("Arial", 10.0f))
    {
        byte charset2 = font2.GdiCharSet;
    }

    // best
    using Font font3 = new Font("Arial", 10.0f);
    byte charset3 = font3.GdiCharSet;
    ```

**[⬆ back to top](#table-of-contents)**

### Operators

  * **Rule:** Use the `&&` and `||` operators instead of `&` and `|`.
  * **Reason:** This avoids unnecessary exceptions and increases performance by skipping the unnecessary comparisons.

    ```c#
    // bad - will cause a run-time error if divisor is 0
    if ((divisor != 0) & (dividend / divisor > 0))
    { ... }
    else
    { ... }

    // good
    if ((divisor != 0) && (dividend / divisor > 0))
    { ... }
    else
    { ... }
    ```

  * **Rule:** Use the concise for of object instantiation with the `new` operator
  * **Reason:** Simplicity!

    ```c#
    // unnecessary
    ExampleClass instance2 = new ExampleClass();

    // better (if C# 8-)
    var instance1 = new ExampleClass();

    // best (C# 9+)
    ExampleClass instance2 = new();
    ```

**[⬆ back to top](#table-of-contents)**

### LINQ Queries

  * **Rules:** 
      * Use clear query names and aliases.
      * Use camelCasing for query names and PascalCasing for aliases.
      * Use implicit typing in the declaration of query variables.
      * Align the query clauses under the `from` clause.
  * **Reason:** Promotes code readability.

    ```c#
    // good
    var localDistributors = from customer in customers
                            join distributor in distributors on customer.City equals distributor.City
                            select new { Customer = customer, Distributor = distributor };
    ```

**[⬆ back to top](#table-of-contents)**

### Dotnet Coding Style

  * **Rules:** 
      * Use [Allman style](https://en.wikipedia.org/wiki/Indentation_style#Allman_style) braces, where each brace begins on a new line.
      * Avoid more than one empty line at any time. For example, do not have two blank lines between members of a type.
      * When using a single-statement `if`, never use single-line form (for example: `if (source == null) throw new ArgumentNullException("source");`).

_Example File_

    ```c#
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using System.Collections.Specialized;
    using System.ComponentModel;
    using System.Diagnostics;
    using Microsoft.Win32;

    namespace System.Collections.Generic
    {
        public partial class ObservableLinkedList<T> : INotifyCollectionChanged, INotifyPropertyChanged
        {
            private ObservableLinkedListNode<T> _head;
            private int _count;

            public ObservableLinkedList(IEnumerable<T> items)
            {
                if (items == null)
                    throw new ArgumentNullException(nameof(items));

                foreach (T item in items)
                {
                    AddLast(item);
                }
            }

            public event NotifyCollectionChangedEventHandler CollectionChanged;

            public int Count
            {
                get { return _count; }
            }

            public ObservableLinkedListNode AddLast(T value)
            {
                var newNode = new LinkedListNode<T>(this, value);

                InsertNodeBefore(_head, node);
            }

            protected virtual void OnCollectionChanged(NotifyCollectionChangedEventArgs e)
            {
                NotifyCollectionChangedEventHandler handler = CollectionChanged;
                if (handler != null)
                {
                    handler(this, e);
                }
            }

            private void InsertNodeBefore(LinkedListNode<T> node, LinkedListNode<T> newNode)
            {
                ...
            }

            ...
        }
    }
    ```

**[⬆ back to top](#table-of-contents)**

### Array vs List

  * **Rule:** Prefer `List<>` over arrays except when the size of the container is fixed and known at construction time or for multidimensional arrays.
  * **Reason:** `List<>` is more flexible then arrays as arrays are of fixed capacity.

**[⬆ back to top](#table-of-contents)**

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

**Style Guides**

  - [Angular Style Guide](https://angular.io/guide/styleguide)
  - [Google Typescript Style Guide](https://google.github.io/styleguide/tsguide.html)
  - [C# Coding Conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
  - [C# Coding Style](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
  - [C# at Google Style Guide](https://google.github.io/styleguide/csharp-style.html)
  - [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwaldron/idiomatic.js)

**Further Reading**

  - [ES6 Features](https://github.com/lukehoban/es6features) - Luke Hoban
  - [Frontend Guidelines](https://github.com/bendc/frontend-guidelines) - Benjamin De Cock
  - [Scripting Best Practices](https://devblogs.microsoft.com/scripting/tag/best-practices/)

**Books**

  - [Advanced TypeScript Programming Projects](https://www.amazon.com/Advanced-TypeScript-Programming-Projects-JavaScript-ebook/dp/B07R8MB288) - Peter O'Hanlon
  - [Effective TypeScript](https://effectivetypescript.com/) - Dan Vanderkam
  - [Essential TypeScript 4](https://www.amazon.com/Essential-TypeScript-4-Beginner-Pro/dp/148427010X) - Adam Freeman
  - [Eloquent JavaScript](https://eloquentjavascript.net/) - Marijn Haverbeke
  - [Angular - The Complete Guide](https://www.oreilly.com/library/view/angular-the/9781788998437/) - Maximilian Schwarzmuller
  - [C# 8.0 and .NET Core 3.0](https://www.amazon.com/8-0-NET-Core-3-0-Cross-Platform-ebook/dp/B07YLXFGBS?tag=guru990f-20&geniuslink=true) - Mark Price
  - [C# 8.0 Pocket Reference: Instant Help for C# 8.0 Programmers](https://www.amazon.com/8-0-Pocket-Reference-Instant-Programmers/dp/1492051217?tag=guru990f-20&geniuslink=true) - Jospeh Albahari 


**[⬆ back to top](#table-of-contents)**

## Copyright

Copyright (c) 2022 The Wizard

**[⬆ back to top](#table-of-contents)**

## Amendments

To propose changes to this style guide please submit a pull request for peer review.

**[⬆ back to top](#table-of-contents)**