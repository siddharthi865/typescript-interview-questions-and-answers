# Set 1

| S.No | Question |
| --- | --- |
| 1 | [What is TypeScript and how is it different from JavaScript?](#question-1-what-is-typescript-and-how-is-it-different-from-javascript) |
| 2 | [What are the advantages of using TypeScript?](#question-2-what-are-the-advantages-of-using-typescript) |
| 3 | [How do you install TypeScript?](#question-3-how-do-you-install-typescript) |
| 4 | [How do you compile TypeScript code to JavaScript?](#question-4-how-do-you-compile-typescript-code-to-javascript) |
| 5 | [Explain the tsconfig.json file and some important options](#question-5-explain-the-tsconfigjson-file-and-some-important-options) |
| 6 | [What are TypeScript basic types? Give examples](#question-6-what-are-typescript-basic-types-give-examples) |
| 7 | [How does TypeScript handle type inference?](#question-7-how-does-typescript-handle-type-inference) |
| 8 | [What is the difference between any, unknown, and never types?](#question-8-what-is-the-difference-between-any-unknown-and-never-types) |
| 9 | [Explain union types with an example](#question-9-explain-union-types-with-an-example) |
| 10 | [Explain intersection types with an example](#question-10-explain-intersection-types-with-an-example) |
| 11 | [What are literal types?](#question-11-what-are-literal-types) |
| 12 | [How do you declare arrays in TypeScript? Give examples](#question-12-how-do-you-declare-arrays-in-typescript-give-examples) |
| 13 | [How do tuples work in TypeScript?](#question-13-how-do-tuples-work-in-typescript) |
| 14 | [What are enums in TypeScript? Explain with examples](#question-14-what-are-enums-in-typescript-explain-with-examples) |
| 15 | [What is the difference between enum and const enum?](#question-15-what-is-the-difference-between-enum-and-const-enum) |
| 16 | [How do you create a function in TypeScript with typed parameters and return type?](#question-16-how-do-you-create-a-function-in-typescript-with-typed-parameters-and-return-type) |
| 17 | [What is the difference between function and arrow functions in TypeScript?](#question-17-what-is-the-difference-between-function-and-arrow-functions-in-typescript) |
| 18 | [How do optional and default parameters work in functions?](#question-18-how-do-optional-and-default-parameters-work-in-functions) |
| 19 | [What is type aliasing? Give an example](#question-19-what-is-type-aliasing-give-an-example) |
| 20 | [What are interfaces in TypeScript? Give an example](#question-20-what-are-interfaces-in-typescript-give-an-example) |

## Question 1. What is TypeScript and how is it different from JavaScript?

TypeScript is a statically typed, superset of JavaScript developed by Microsoft.

It adds optional static typing, interfaces, enums, generics, and advanced tooling on top of JavaScript, while still compiling down to plain JavaScript
that runs in any browser or Node.js environment.

_TypeScript helps us catch errors at compile time that would otherwise appear at runtime in JavaScript._

### How TypeScript Works Internally

TypeScript code is not executed directly by the browser or Node.js.

Instead, it goes through a compile step:

```bash
TypeScript (.ts) → TypeScript Compiler (tsc) → JavaScript (.js)
```

So at runtime, there is no TypeScript, only JavaScript.

### Key Differences Between TypeScript and JavaScript

1. **Typing System (Static vs Dynamic)**

    JavaScript is dynamically typed, while Typescript is statically typed.

    TypeScript catches type-related bugs before execution.

    ```js
    // Javascript

    let value = 10;
    value = "hello"; // allowed, no error
    ```

    ```ts
    //Typescript

    let value: number = 10;
    value = "hello"; // Compile-time error
    ```

2. **Compile-Time Error Checking**

    JavaScript errors are mostly discovered at runtime, while typescript prevents this.

    ```js
    // Javascript

    function add(a, b) {
      return a + b;
    }

    add("2", 3); // "23" — logical bug, no error
    ```

    ```ts
    //Typescript

    function add(a: number, b: number): number {
      return a + b;
    }

    add("2", 3); // ❌ Type error during compilation
    ```

3. **Advanced Type Features (Not in JavaScript)**

    TypeScript provides features that don’t exist in JavaScript:

    ```ts
    interface User {
      id: number;
      name: string;
    }

    function getUser(user: User) {
      return user.name;
    }
    ```

    Other examples:
    - Interfaces
    - Enums
    - Generics
    - Union & Intersection types
    - Utility types (`Partial`, `Pick`, `Omit` etc.)

    These features improve **code clarity and maintainability**.

4. **Better Tooling & Developer Experience**

    TypeScript enables:
    - Auto-completion (IntelliSense)
    - Safe refactoring
    - Better navigation
    - Early error highlighting

    In JavaScript, tooling is more limited and often relies on runtime assumptions.

5. **Scalability & Maintainability**

    JavaScript is great for small scripts and quick prototyping.

    TypeScript is better for large-scale applications where:
    - Multiple developers work together
    - Codebase grows over time
    - Strict contracts are required

    This is why most enterprise frameworks (Angular, NestJS) are built with TypeScript.

6. **Backward Compatibility**

    TypeScript is a superset of JavaScript, so every valid JavaScript code is also valid TypeScript.

_**JavaScript gives flexibility, but TypeScript adds safety and scalability. TypeScript helpscatch bugs early, improves maintainability, and makes large codebases easier tomanage without changing JavaScript’s runtime behavior.**_

## Question 2. What are the advantages of using TypeScript?

_**TypeScript improves code quality, developer productivity, and scalability by adding static typing and powerful tooling to JavaScript—without changing runtime behavior.**_

## Question 3. How do you install TypeScript?

_**In real-world projects, I prefer installing TypeScript locally as a dev dependency and using npx tsc, which ensures consistent compiler versions across environments.**_

## Question 4. How do you compile TypeScript code to JavaScript?

## Question 5. Explain the tsconfig.json file and some important options

## Question 6. What are TypeScript basic types? Give examples

## Question 7. How does TypeScript handle type inference?

## Question 8. What is the difference between any, unknown, and never types?

## Question 9. Explain union types with an example

## Question 10. Explain intersection types with an example

## Question 11. What are literal types?

## Question 12. How do you declare arrays in TypeScript? Give examples

## Question 13. How do tuples work in TypeScript?

## Question 14. What are enums in TypeScript? Explain with examples

## Question 15. What is the difference between enum and const enum?

## Question 16. How do you create a function in TypeScript with typed parameters and return type?

## Question 17. What is the difference between function and arrow functions in TypeScript?

## Question 18. How do optional and default parameters work in functions?

## Question 19. What is type aliasing? Give an example

A type alias allows you to create a new name for any type, including:

- Primitive types
- Union types
- Objects
- Tuples
- Function types

**Simple Type Alias Syntax:**

`type AliasName = Type;`

1. **Simple Type Alias**

   ```ts
   type ID = number | string;

   let userId: ID;

   userId = 101; //valid
   userId = "102"; //valid
   userId = true; //error
   ```

   _Here, `ID` is a type alias for `number | string`._

2. **Type Alias for Object**

   ```ts
   type User = { id: number; name: string; isActive: boolean };

   const user: User = { id: 1, name: "Alice", isActive: true };
   ```

   _Makes object types **reusable and readable**._

3. **Type Alias for Function**

   ```ts
   type MathOperation = (a: number, b: number) => number;

   const add: MathOperation = (x, y) => x + y;
   const multiply: MathOperation = (x, y) => x * y;
   ```

   _Reusable function signatures for callbacks or higher-order functions._

4. **Type Alias with Union & Literal Types**

   ```ts
   type Status = "success" | "error" | "loading";

   function printStatus(status: Status) {
     console.log(`Status: ${status}`);
   }

   printStatus("success"); //✅
   printStatus("done"); //❌ Error
   ```

## Question 20. What are interfaces in TypeScript? Give an example

An interface is a custom type definition used to describe the structure of objects, classes or functions.

It’s like a contract — any object or class that implements the interface must satisfy its structure.

1. **Basic Interface Example**

   ```ts
   interface User {
     id: number;
     name: string;
     isActive: boolean;
   }

   const user1: User = {
     id: 1,
     name: "Alice",
     isActive: true,
   };
   ```

   Here, `User` defines the shape of a user object.

2. **Optional Properties**

3. **Readonly Properties**

4. **Methods in Interfaces**

5. **Extending Interfaces**
