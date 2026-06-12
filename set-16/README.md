# Set 16

| S.No. | Question                                                                                                                                                                              |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [What is the difference between TypeScript and JavaScript in terms of type checking?](#question-1-what-is-the-difference-between-typescript-and-javascript-in-terms-of-type-checking) |
| 2.    | [How do you configure TypeScript to target different ECMAScript versions?](#question-2-how-do-you-configure-typescript-to-target-different-ecmascript-versions)                       |
| 3.    | [How do you enable source maps in TypeScript?](#question-3-how-do-you-enable-source-maps-in-typescript)                                                                               |
| 4.    | [What is the difference between `tsc` and `ts-node`?](#question-4-what-is-the-difference-between-tsc-and-ts-node)                                                                     |
| 5.    | [How do you compile TypeScript in watch mode?](#question-5-how-do-you-compile-typescript-in-watch-mode)                                                                               |
| 6.    | [How do you define a literal type for a union of strings?](#question-6-how-do-you-define-a-literal-type-for-a-union-of-strings)                                                       |
| 7.    | [How do you define an array of union types?](#question-7-how-do-you-define-an-array-of-union-types)                                                                                   |
| 8.    | [How do you create a tuple with optional elements?](#question-8-how-do-you-create-a-tuple-with-optional-elements)                                                                     |
| 9.    | [How do you define a tuple with a rest element?](#question-9-how-do-you-define-a-tuple-with-a-rest-element)                                                                           |
| 10.   | [How do you use default parameters in TypeScript functions?](#question-10-how-do-you-use-default-parameters-in-typescript-functions)                                                  |
| 11.   | [How do you type an object with dynamic keys?](#question-11-how-do-you-type-an-object-with-dynamic-keys)                                                                              |
| 12.   | [How do you define an interface with optional and required properties?](#question-12-how-do-you-define-an-interface-with-optional-and-required-properties)                            |
| 13.   | [How do you define a readonly interface property?](#question-13-how-do-you-define-a-readonly-interface-property)                                                                      |
| 14.   | [How do you define an enum with string values?](#question-14-how-do-you-define-an-enum-with-string-values)                                                                            |
| 15.   | [How do you define a numeric enum and access its reverse mapping?](#question-15-how-do-you-define-a-numeric-enum-and-access-its-reverse-mapping)                                      |
| 16.   | [How do you define a constant variable in TypeScript?](#question-16-how-do-you-define-a-constant-variable-in-typescript)                                                              |
| 17.   | [How do you define a variable whose type is inferred?](#question-17-how-do-you-define-a-variable-whose-type-is-inferred)                                                              |
| 18.   | [How do you declare a function that returns `void`?](#question-18-how-do-you-declare-a-function-that-returns-void)                                                                    |
| 19.   | [How do you declare a function that never returns?](#question-19-how-do-you-declare-a-function-that-never-returns)                                                                    |
| 20.   | [How do you define an interface with a method signature?](#question-20-how-do-you-define-an-interface-with-a-method-signature)                                                        |

## Question 1. What is the difference between TypeScript and JavaScript in terms of type checking?

## Short answer

JavaScript is dynamically typed and performs type checking at runtime, whereas TypeScript is statically typed and performs type checking at compile time (before execution).

---

## Explanation

The key difference lies in **when and how type checking happens**:

### JavaScript (Dynamic Typing)

- Types are associated with **values, not variables**.
- Type checking happens **at runtime**.
- Errors like passing a string where a number is expected only appear when the code executes.

This makes JavaScript flexible but more error-prone in large systems.

---

### TypeScript (Static Typing)

- Types are associated with **variables and expressions at development time**.
- Type checking happens **at compile time** via the TypeScript compiler (`tsc`).
- It prevents many classes of bugs before code runs.

TypeScript is essentially a **superset of JavaScript** that adds a static type system and compiles down to plain JavaScript.

---

### Key implication for engineering design

- JavaScript prioritizes **flexibility and runtime dynamism**.
- TypeScript prioritizes **predictability, maintainability, and scalability**.
- In large codebases, TypeScript shifts error detection earlier in the development lifecycle, reducing production risk.

---

## Example

### JavaScript (runtime error)

```js
function add(a, b) {
  return a + b;
}

console.log(add(5, "10"));
// Output: "510" (unexpected string concatenation)
```

No error is thrown until runtime, and behavior may be unintended.

---

### TypeScript (compile-time safety)

```ts
function add(a: number, b: number): number {
  return a + b;
}

console.log(add(5, "10"));
// ❌ Error: Argument of type 'string' is not assignable to parameter of type 'number'
```

The error is caught **before execution**, during compilation.

---

## Pitfalls

- TypeScript types are **erased at runtime**, so runtime validation still requires additional tools (e.g., Zod, io-ts).
- Over-reliance on `any` can effectively downgrade TypeScript back to JavaScript.
- JS flexibility (dynamic properties, monkey patching) can conflict with strict typing assumptions.
- Misconfigured `tsconfig` (e.g., disabled `strict`) reduces TypeScript’s safety guarantees.

## Question 2. How do you configure TypeScript to target different ECMAScript versions?

## Question 3. How do you enable source maps in TypeScript?

## Question 4. What is the difference between `tsc` and `ts-node`?

## Question 5. How do you compile TypeScript in watch mode?

## Question 6. How do you define a literal type for a union of strings?

## Question 7. How do you define an array of union types?

## Question 8. How do you create a tuple with optional elements?

## Question 9. How do you define a tuple with a rest element?

## Question 10. How do you use default parameters in TypeScript functions?

## Question 11. How do you type an object with dynamic keys?

## Question 12. How do you define an interface with optional and required properties?

## Question 13. How do you define a readonly interface property?

## Question 14. How do you define an enum with string values?

## Question 15. How do you define a numeric enum and access its reverse mapping?

## Question 16. How do you define a constant variable in TypeScript?

## Question 17. How do you define a variable whose type is inferred?

## Question 18. How do you declare a function that returns `void`?

## Question 19. How do you declare a function that never returns?

## Question 20. How do you define an interface with a method signature?
