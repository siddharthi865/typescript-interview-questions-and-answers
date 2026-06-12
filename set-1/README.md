# Set 1

| S.No | Question                                                                                                                                                                           |
| ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1    | [What is TypeScript and how is it different from JavaScript?](#question-1-what-is-typescript-and-how-is-it-different-from-javascript)                                              |
| 2    | [What are the advantages of using TypeScript?](#question-2-what-are-the-advantages-of-using-typescript)                                                                            |
| 3    | [How do you install TypeScript?](#question-3-how-do-you-install-typescript)                                                                                                        |
| 4    | [How do you compile TypeScript code to JavaScript?](#question-4-how-do-you-compile-typescript-code-to-javascript)                                                                  |
| 5    | [Explain the tsconfig.json file and some important options](#question-5-explain-the-tsconfigjson-file-and-some-important-options)                                                  |
| 6    | [What are TypeScript basic types? Give examples](#question-6-what-are-typescript-basic-types-give-examples)                                                                        |
| 7    | [How does TypeScript handle type inference?](#question-7-how-does-typescript-handle-type-inference)                                                                                |
| 8    | [What is the difference between any, unknown, and never types?](#question-8-what-is-the-difference-between-any-unknown-and-never-types)                                            |
| 9    | [Explain union types with an example](#question-9-explain-union-types-with-an-example)                                                                                             |
| 10   | [Explain intersection types with an example](#question-10-explain-intersection-types-with-an-example)                                                                              |
| 11   | [What are literal types?](#question-11-what-are-literal-types)                                                                                                                     |
| 12   | [How do you declare arrays in TypeScript? Give examples](#question-12-how-do-you-declare-arrays-in-typescript-give-examples)                                                       |
| 13   | [How do tuples work in TypeScript?](#question-13-how-do-tuples-work-in-typescript)                                                                                                 |
| 14   | [What are enums in TypeScript? Explain with examples](#question-14-what-are-enums-in-typescript-explain-with-examples)                                                             |
| 15   | [What is the difference between enum and const enum?](#question-15-what-is-the-difference-between-enum-and-const-enum)                                                             |
| 16   | [How do you create a function in TypeScript with typed parameters and return type?](#question-16-how-do-you-create-a-function-in-typescript-with-typed-parameters-and-return-type) |
| 17   | [What is the difference between function and arrow functions in TypeScript?](#question-17-what-is-the-difference-between-function-and-arrow-functions-in-typescript)               |
| 18   | [How do optional and default parameters work in functions?](#question-18-how-do-optional-and-default-parameters-work-in-functions)                                                 |
| 19   | [What is type aliasing? Give an example](#question-19-what-is-type-aliasing-give-an-example)                                                                                       |
| 20   | [What are interfaces in TypeScript? Give an example](#question-20-what-are-interfaces-in-typescript-give-an-example)                                                               |

## Question 1. What is TypeScript and how is it different from JavaScript?

## Short answer

TypeScript is a statically typed superset of JavaScript that adds optional type checking and advanced language features, which are compiled (transpiled) into plain JavaScript before execution.

---

## Explanation

TypeScript (TS) extends JavaScript (JS) by introducing a **type system and compile-time checks**, while still ultimately producing standard JavaScript that runs anywhere JS runs (browser, Node.js, etc.).

### Key differences:

#### 1. Type system

- **JavaScript:** Dynamically typed (types resolved at runtime)
- **TypeScript:** Statically typed (types checked at compile time)

This means TS catches many errors before code runs.

#### 2. Compilation step

- JS runs directly in runtime environments
- TS must be compiled (transpiled) to JS using `tsc`

#### 3. Tooling and IDE support

TypeScript provides:

- Better autocomplete
- Safer refactoring
- Inline type errors
- Enhanced navigation

#### 4. Language features

TypeScript adds:

- Interfaces
- Generics
- Enums
- Tuples
- Advanced type inference
- Utility types (`Partial`, `Pick`, etc.)

#### 5. Compatibility

- TypeScript is fully compatible with JavaScript
- Any valid JS file is valid TS (gradual adoption)

---

### Design implications (senior-level view)

TypeScript is not just “JavaScript with types” — it’s a **compile-time safety layer over a dynamic runtime system**.

This creates trade-offs:

- **Safety vs flexibility:** stricter contracts reduce runtime bugs but add design overhead
- **Build complexity:** introduces compilation step and tooling pipeline
- **Type system expressiveness:** enables domain modeling but can become complex if overused
- **Runtime mismatch risk:** types exist only at compile time, not at runtime

---

## Example

### JavaScript (dynamic typing)

```js
function add(a, b) {
  return a + b;
}

add(1, 2); // 3
add(1, "2"); // "12" (bug-prone behavior)
```

### TypeScript (static typing)

```ts
function add(a: number, b: number): number {
  return a + b;
}

add(1, 2); // OK
// add(1, "2"); // Error: Argument of type 'string' is not assignable to parameter of type 'number'
```

---

## Pitfalls

- **False sense of safety:** TypeScript does not validate runtime data (e.g., API responses still need validation)
- **Overengineering types:** complex type gymnastics can reduce maintainability
- **Any leakage:** overuse of `any` defeats the purpose of TypeScript
- **Build-time only checks:** issues can still occur at runtime if not validated properly
- **Mismatch with backend/runtime data:** especially with JSON APIs

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
