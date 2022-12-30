<div id="top"></div>

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="../assets/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h2 align="center">A Hobbit's Developer C♯ Style Guide</h2>

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
    <li><a href="#c♯-style-guide">C♯ Style Guide</a></li>
      <ul>
        <li><a href="#note-on-consistency">Note on Consistency</a></li>
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


# C♯ Style Guide

This section is derived from the official [Microsoft C# Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/). It contains highlights that C# developers should consider following - unless you have a significant reason to deviate. Again this is not comprehensive of all rules recommended in the official documentation but the spark notes version. 

  * **#1 Rule:** Use Visual Studio Defaults!"

## Note on Consistency

For any style question that isn't settled definitively by this styleguide, do what the other code in the same file is already doing (be consistent). If that doesn't resolve the question, consider emulating the other files in the same directory. At all times, remember that code reviewers should not focus on simply enforcing the rules in this styleguide, but instead focus on improving overall code quality.

**[⬆ back to top](#table-of-contents)**

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
  * **Reason:** Conde simplicity helps with code readability.

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
      * Avoid `this.` unless absolutely necessary.
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

# Resources


**Read This**

  - [C# Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/?WT.mc_id=dotnet-35129-website)
  - [C# Coding Conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
  - [C# Coding Style](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
  - [C# at Google Style Guide](https://google.github.io/styleguide/csharp-style.html)

**Tools**

  - Internal Server-side Frameworks
    - [Entity Framework Core](https://learn.microsoft.com/en-us/ef/core/)
    - [ASP.NET](https://learn.microsoft.com/en-us/aspnet/core/?WT.mc_id=dotnet-35129-website&view=aspnetcore-7.0)

**Books**

  - [C# 8.0 and .NET Core 3.0](https://www.amazon.com/8-0-NET-Core-3-0-Cross-Platform-ebook/dp/B07YLXFGBS?tag=guru990f-20&geniuslink=true) - Mark Price
  - [C# 8.0 Pocket Reference: Instant Help for C# 8.0 Programmers](https://www.amazon.com/8-0-Pocket-Reference-Instant-Programmers/dp/1492051217?tag=guru990f-20&geniuslink=true) - Jospeh Albahari 


**[⬆ back to top](#table-of-contents)**

# Copyright

Copyright (c) 2022 The Wizard

**[⬆ back to top](#table-of-contents)**

# Amendments

To propose changes to this style guide please submit a pull request for peer review.

**[⬆ back to top](#table-of-contents)**