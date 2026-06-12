# Set 24

| S.No. | Question                                                                                                                                                                              |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you type a function pipeline with multiple input/output types?](#question-1-how-do-you-type-a-function-pipeline-with-multiple-inputoutput-types)                              |
| 2.    | [How do you implement type-safe default props in React?](#question-2-how-do-you-implement-type-safe-default-props-in-react)                                                           |
| 3.    | [How do you type a function that can return multiple specific object shapes?](#question-3-how-do-you-type-a-function-that-can-return-multiple-specific-object-shapes)                 |
| 4.    | [How do you implement discriminated unions with exhaustive checking?](#question-4-how-do-you-implement-discriminated-unions-with-exhaustive-checking)                                 |
| 5.    | [How do you type API responses with optional and required fields?](#question-5-how-do-you-type-api-responses-with-optional-and-required-fields)                                       |
| 6.    | [How do you type a function accepting a configuration object with optional generics?](#question-6-how-do-you-type-a-function-accepting-a-configuration-object-with-optional-generics) |
| 7.    | [How do you type arrays with conditional types?](#question-7-how-do-you-type-arrays-with-conditional-types)                                                                           |
| 8.    | [How do you type objects with dynamic keys and generic values?](#question-8-how-do-you-type-objects-with-dynamic-keys-and-generic-values)                                             |
| 9.    | [How do you type a callback function that itself returns a generic function?](#question-9-how-do-you-type-a-callback-function-that-itself-returns-a-generic-function)                 |
| 10.   | [How do you type nested React props generically?](#question-10-how-do-you-type-nested-react-props-generically)                                                                        |
| 11.   | [How do you implement recursive conditional types?](#question-11-how-do-you-implement-recursive-conditional-types)                                                                    |
| 12.   | [How do you implement template literal types for string manipulation?](#question-12-how-do-you-implement-template-literal-types-for-string-manipulation)                              |
| 13.   | [How do you implement type inference using `infer` keyword?](#question-13-how-do-you-implement-type-inference-using-infer-keyword)                                                    |
| 14.   | [How do you implement recursive mapped types?](#question-14-how-do-you-implement-recursive-mapped-types)                                                                              |
| 15.   | [How do you implement discriminated union types with exhaustive checking?](#question-15-how-do-you-implement-discriminated-union-types-with-exhaustive-checking)                      |
| 16.   | [How do you implement type-safe event emitters with generics?](#question-16-how-do-you-implement-type-safe-event-emitters-with-generics)                                              |
| 17.   | [How do you implement type-safe middleware in Node.js?](#question-17-how-do-you-implement-type-safe-middleware-in-nodejs)                                                             |
| 18.   | [How do you type GraphQL resolvers in TypeScript?](#question-18-how-do-you-type-graphql-resolvers-in-typescript)                                                                      |
| 19.   | [How do you type Prisma ORM queries in TypeScript?](#question-19-how-do-you-type-prisma-orm-queries-in-typescript)                                                                    |
| 20.   | [How do you implement type-safe API request/response layers?](#question-20-how-do-you-implement-type-safe-api-requestresponse-layers)                                                 |

## Question 1. How do you type a function pipeline with multiple input/output types?

## Short answer

You type a function pipeline using **variadic tuple types + generics** so each function’s output is inferred as the next function’s input in a strongly-typed chain.

---

## Explanation

A function pipeline is a composition of functions where each function transforms a value and passes it to the next. The key TypeScript challenge is preserving **type continuity across multiple functions**, especially when the number of steps is dynamic.

Modern TypeScript solves this using:

- **Variadic tuple types** (`[A, B, C, ...]`) to represent a sequence of functions
- **Recursive conditional types** to validate and compute output types step-by-step
- **Generic inference (`infer`)** to extract input/output types of each function
- A strongly-typed `pipe` utility that enforces:
  - First function input matches initial value
  - Each subsequent function accepts the previous output

Design-wise, this gives:

- Compile-time correctness of pipelines
- Excellent inference for complex functional flows
- Zero runtime overhead

Trade-off: complex type definitions can reduce readability and slow TS compiler slightly for very large pipelines.

---

## Example

```ts
type AnyFn = (arg: any) => any;

type Pipe<TInput, TFns extends [AnyFn, ...AnyFn[]]> = TFns extends [
  (arg: TInput) => infer R,
  ...infer Rest extends AnyFn[],
]
  ? Rest extends []
    ? R
    : Pipe<R, Rest>
  : never;

function pipe<TInput, TFns extends [AnyFn, ...AnyFn[]]>(
  input: TInput,
  ...fns: TFns
): Pipe<TInput, TFns> {
  return fns.reduce((acc, fn) => fn(acc), input) as any;
}

// Usage
const result = pipe(
  "123",
  (s: string) => s.length,
  (n: number) => n * 2,
  (x: number) => x.toString(),
);

// result is inferred as string
```

---

## Pitfalls

- Recursive types can hit **TypeScript instantiation depth limits** in large pipelines.
- Poor inference if functions are loosely typed (`any` breaks chain safety).
- Error messages become hard to read in deeply nested pipelines.
- Overuse of complex conditional types can slow compiler performance.
- Mixing overloaded functions may break inference unless explicitly typed.

## Question 2. How do you implement type-safe default props in React?

## Question 3. How do you type a function that can return multiple specific object shapes?

## Question 4. How do you implement discriminated unions with exhaustive checking?

## Question 5. How do you type API responses with optional and required fields?

## Question 6. How do you type a function accepting a configuration object with optional generics?

## Question 7. How do you type arrays with conditional types?

## Question 8. How do you type objects with dynamic keys and generic values?

## Question 9. How do you type a callback function that itself returns a generic function?

## Question 10. How do you type nested React props generically?

## Question 11. How do you implement recursive conditional types?

## Question 12. How do you implement template literal types for string manipulation?

## Question 13. How do you implement type inference using `infer` keyword?

## Question 14. How do you implement recursive mapped types?

## Question 15. How do you implement discriminated union types with exhaustive checking?

## Question 16. How do you implement type-safe event emitters with generics?

## Question 17. How do you implement type-safe middleware in Node.js?

## Question 18. How do you type GraphQL resolvers in TypeScript?

## Question 19. How do you type Prisma ORM queries in TypeScript?

## Question 20. How do you implement type-safe API request/response layers?
