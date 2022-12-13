<div id="top"></div>

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h2 align="center">A Hobbit's Developer Style Guide</h2>

  <p align="center">
    A style guide for the layman developer.
    <br />
    <a href="https://github.com/coltskeen/Style-Guide/issues">Report Bug</a>
    ·
    <a href="https://github.com/coltskeen/Style-Guide/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

# Style Guide

> ### "Arguments over style are pointless. There should be a style guide, and you should follow it"
> &emsp;_Rebecca_ _Murphey_

## Table of Contents

  1. [Types](#types)
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
  1. [Variables](#variables)
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
  1. [Resources](#resources)
  1. [Copyright](#copyright)
  1. [Amendments](#amendments)

  1. [Variable](#variable-and-function)
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