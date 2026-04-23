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

## Question 2. What are the advantages of using TypeScript?

## Question 3. How do you install TypeScript?

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

## Question 20. What are interfaces in TypeScript? Give an example.
