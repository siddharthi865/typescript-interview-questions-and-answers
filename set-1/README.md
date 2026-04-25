# Set 1

## Question 1. What is TypeScript and how is it different from JavaScript?

TypeScript is a statically typed, superset of JavaScript developed by Microsoft.

It adds optional static typing, interfaces, enums, generics, and advanced tooling on top of JavaScript, while still compiling down to plain JavaScript
that runs in any browser or Node.js environment.

<i> TypeScript helps us catch errors at compile time that would otherwise appear at runtime in JavaScript. </i>

### How TypeScript Works Internally

TypeScript code is not executed directly by the browser or Node.js.

Instead, it goes through a compile step:

```bash
TypeScript (.ts) → TypeScript Compiler (tsc) → JavaScript (.js)
```

So at runtime, there is no TypeScript, only JavaScript.

### Key Differences Between TypeScript and JavaScript:

1.  **Typing System (Static vs Dynamic)**

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

2.  **Compile-Time Error Checking**

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

3.  **Advanced Type Features (Not in JavaScript)**

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
    - Utility types (<code>Partial</code>, <code>Pick</code>, <code>Omit</code> etc.)

    These features improve **code clarity and maintainability**.

4.  **Better Tooling & Developer Experience**

    TypeScript enables:
    - Auto-completion (IntelliSense)
    - Safe refactoring
    - Better navigation
    - Early error highlighting

    In JavaScript, tooling is more limited and often relies on runtime assumptions.

5.  **Scalability & Maintainability**

    JavaScript is great for small scripts and quick prototyping.

    TypeScript is better for large-scale applications where:
    - Multiple developers work together
    - Codebase grows over time
    - Strict contracts are required

    This is why most enterprise frameworks (Angular, NestJS) are built with TypeScript.

6.  **Backward Compatibility**

    TypeScript is a superset of JavaScript, so every valid JavaScript code is also valid TypeScript.

<i>**JavaScript gives flexibility, but TypeScript adds safety and scalability. TypeScript helpscatch bugs early, improves maintainability, and makes large codebases easier tomanage without changing JavaScript’s runtime behavior.**</i>

## Question 2. What are the advantages of using TypeScript?

<i>**TypeScript improves code quality, developer productivity, and scalability by adding static typing and powerful tooling to JavaScript—without changing runtime behavior.**</i>

## Question 3. How do you install TypeScript?

<i>**In real-world projects, I prefer installing TypeScript locally as a dev dependency and using npx tsc, which ensures consistent compiler versions across environments.**</i>

## Question 4. How do you compile TypeScript code to JavaScript?

## Question 5. Explain the tsconfig.json file and some important options.

## Question 6. What are TypeScript basic types? Give examples.

## Question 7. How does TypeScript handle type inference?

## Question 8. What is the diff erence between any, unknown, and never types?

## Question 9. Explain union types with an example.

## Question 10. Explain intersection types with an example.

## Question 11. What are literal types?

## Question 12. How do you declare arrays in TypeScript? Give examples.

## Question 13. How do tuples work in TypeScript?

## Question 14. What are enums in TypeScript? Explain with examples.

## Question 15. What is the difference between enum and const enum?

## Question 16. How do you create a function in TypeScript with typed parameters and return type?

## Question 17. What is the difference between function and arrow functions in TypeScript?

## Question 18. How do optional and default parameters work in functions?

## Question 19. What is type aliasing? Give an example.

A type alias allows you to create a new name for any type, including:

- Primitive types
- Union types
- Objects
- Tuples
- Function types

**Simple Type Alias Syntax:**

<code>type AliasName = Type;</code>

1. **Simple Type Alias**

   ```ts
   type ID = number | string;

   let userId: ID;

   userId = 101; //valid
   userId = "102"; //valid
   userId = true; //error
   ```

   <i>Here, <code>ID</code> is a type alias for <code>number | string</code>.</i>

2. **Type Alias for Object**

   ```ts
   type User = { id: number; name: string; isActive: boolean };

   const user: User = { id: 1, name: "Alice", isActive: true };
   ```

   <i>Makes object types **reusable and readable**.</i>

3. **Type Alias for Function**

   ```ts
   type MathOperation = (a: number, b: number) => number;

   const add: MathOperation = (x, y) => x + y;
   const multiply: MathOperation = (x, y) => x * y;
   ```

   <i>Reusable function signatures for callbacks or higher-order functions.</i>

4. **Type Alias with Union & Literal Types**

   ```ts
   type Status = "success" | "error" | "loading";

   function printStatus(status: Status) {
     console.log(`Status: ${status}`);
   }

   printStatus("success"); //✅
   printStatus("done"); //❌ Error
   ```

## Question 20. What are interfaces in TypeScript? Give an example.

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

   Here, <code>User</code> defines the shape of a user object.

2. **Optional Properties**

3. **Readonly Properties**

4. **Methods in Interfaces**

5. **Extending Interfaces**
