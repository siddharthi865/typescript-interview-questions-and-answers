# Set 19

| S.No. | Question                                                                                                                                                                                  |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you type a rest parameter function with generics?](#question-1-how-do-you-type-a-rest-parameter-function-with-generics)                                                           |
| 2.    | [How do you type a reducer function in React with discriminated unions?](#question-2-how-do-you-type-a-reducer-function-in-react-with-discriminated-unions)                               |
| 3.    | [How do you type `useState` in React with generics?](#question-3-how-do-you-type-usestate-in-react-with-generics)                                                                         |
| 4.    | [How do you type `useRef` in React for DOM elements?](#question-4-how-do-you-type-useref-in-react-for-dom-elements)                                                                       |
| 5.    | [How do you type `useReducer` with state and action generics?](#question-5-how-do-you-type-usereducer-with-state-and-action-generics)                                                     |
| 6.    | [How do you type `useEffect` dependencies correctly?](#question-6-how-do-you-type-useeffect-dependencies-correctly)                                                                       |
| 7.    | [How do you type a function that returns a Promise of multiple types?](#question-7-how-do-you-type-a-function-that-returns-a-promise-of-multiple-types)                                   |
| 8.    | [How do you type an API response with optional and required fields?](#question-8-how-do-you-type-an-api-response-with-optional-and-required-fields)                                       |
| 9.    | [How do you type a function accepting another function with different parameter types?](#question-9-how-do-you-type-a-function-accepting-another-function-with-different-parameter-types) |
| 10.   | [How do you implement type-safe higher-order functions?](#question-10-how-do-you-implement-type-safe-higher-order-functions)                                                              |
| 11.   | [How do you implement recursive conditional types?](#question-11-how-do-you-implement-recursive-conditional-types)                                                                        |
| 12.   | [How do you implement template literal types?](#question-12-how-do-you-implement-template-literal-types)                                                                                  |
| 13.   | [How do you implement type inference with `infer` keyword?](#question-13-how-do-you-implement-type-inference-with-infer-keyword)                                                          |
| 14.   | [How do you implement recursive generics for tree structures?](#question-14-how-do-you-implement-recursive-generics-for-tree-structures)                                                  |
| 15.   | [How do you implement discriminated union types with exhaustive checking?](#question-15-how-do-you-implement-discriminated-union-types-with-exhaustive-checking)                          |
| 16.   | [How do you implement type-safe event emitters with generics?](#question-16-how-do-you-implement-type-safe-event-emitters-with-generics)                                                  |
| 17.   | [How do you implement type-safe middleware in Node.js?](#question-17-how-do-you-implement-type-safe-middleware-in-nodejs)                                                                 |
| 18.   | [How do you type GraphQL resolvers in TypeScript?](#question-18-how-do-you-type-graphql-resolvers-in-typescript)                                                                          |
| 19.   | [How do you type Prisma queries in TypeScript?](#question-19-how-do-you-type-prisma-queries-in-typescript)                                                                                |
| 20.   | [How do you implement type-safe API request/response layers?](#question-20-how-do-you-implement-type-safe-api-requestresponse-layers)                                                     |

## Question 1. How do you type a rest parameter function with generics?

## Short answer

You type a rest-parameter function with generics by declaring the generic parameter(s) on the function and typing the rest parameter as a generic tuple or array type (often using variadic tuple types for precise inference).

---

## Explanation

In TypeScript, rest parameters (`...args`) can be typed as either a generic array (`T[]`) or, more powerfully, a **variadic tuple type** (`T extends any[]`) when you want to preserve exact argument shapes.

There are two common levels of sophistication:

### 1. Simple generic rest parameter (homogeneous)

Use this when all arguments share the same type:

```ts
function collect<T>(...items: T[]): T[] {
  return items;
}
```

- `T` is inferred from all arguments
- Loss: you don’t preserve positional types

---

### 2. Variadic tuple generics (recommended for real-world APIs)

Use this when you want to preserve argument structure and types precisely:

```ts
function callWithLogging<T extends unknown[], R>(
  fn: (...args: T) => R,
  ...args: T
): R {
  console.log("Calling with:", args);
  return fn(...args);
}
```

Here:

- `T` captures the entire argument tuple
- `...args: T` ensures exact preservation of types and order
- `R` represents return type

This pattern is foundational for utility types like `Parameters<T>` and `ConstructorParameters<T>`.

---

### Why this matters

Without tuple inference, you lose:

- argument position safety
- literal type preservation
- overload fidelity

With variadic tuples, TypeScript can infer:

```ts
callWithLogging((a: number, b: string) => a + b.length, 10, "hello");
```

`T = [number, string]` — fully preserved.

---

## Example

```ts
function debounce<T extends (...args: any[]) => any>(
  fn: T,
  delay: number,
): (...args: Parameters<T>) => void {
  let timeout: ReturnType<typeof setTimeout>;

  return (...args: Parameters<T>) => {
    clearTimeout(timeout);
    timeout = setTimeout(() => fn(...args), delay);
  };
}

// Usage
const log = (msg: string, count: number) => {
  console.log(msg, count);
};

const debouncedLog = debounce(log, 300);

debouncedLog("hello", 42);
```

Key idea: `Parameters<T>` extracts a tuple of arguments and reuses it in the rest parameter.

---

## Pitfalls

- **Overusing `any[]` loses inference quality**
  - You lose tuple precision and autocomplete benefits

- **Not constraining generics properly**
  - `T extends any[]` or `T extends unknown[]` is required for tuple capture

- **Rest parameter widening**
  - `...args: T[]` is wrong when `T` is already an array type (double array issue)

- **Inference collapse in complex higher-order functions**
  - Deep generic compositions may degrade to `unknown[]`

- **Compatibility**
  - Variadic tuple improvements are best in TS 4.0+; older versions had weaker inference

## Question 2. How do you type a reducer function in React with discriminated unions?

## Question 3. How do you type `useState` in React with generics?

## Question 4. How do you type `useRef` in React for DOM elements?

## Question 5. How do you type `useReducer` with state and action generics?

## Question 6. How do you type `useEffect` dependencies correctly?

## Question 7. How do you type a function that returns a Promise of multiple types?

## Question 8. How do you type an API response with optional and required fields?

## Question 9. How do you type a function accepting another function with different parameter types?

## Question 10. How do you implement type-safe higher-order functions?

## Question 11. How do you implement recursive conditional types?

## Question 12. How do you implement template literal types?

## Question 13. How do you implement type inference with `infer` keyword?

## Question 14. How do you implement recursive generics for tree structures?

## Question 15. How do you implement discriminated union types with exhaustive checking?

## Question 16. How do you implement type-safe event emitters with generics?

## Question 17. How do you implement type-safe middleware in Node.js?

## Question 18. How do you type GraphQL resolvers in TypeScript?

## Question 19. How do you type Prisma queries in TypeScript?

## Question 20. How do you implement type-safe API request/response layers?
