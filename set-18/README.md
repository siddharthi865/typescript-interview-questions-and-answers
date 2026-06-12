# Set 18

| S.No. | Question                                                                                                                               |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you define conditional types?](#question-1-how-do-you-define-conditional-types)                                                |
| 2.    | [How do you implement `Partial<T>` for nested objects?](#question-2-how-do-you-implement-partialt-for-nested-objects)                  |
| 3.    | [How do you implement `Required<T>` for nested objects?](#question-3-how-do-you-implement-requiredt-for-nested-objects)                |
| 4.    | [How do you implement `Pick<T, K>`?](#question-4-how-do-you-implement-pickt-k)                                                         |
| 5.    | [How do you define an `Omit<T, K>` type?](#question-5-how-do-you-define-an-omitt-k-type)                                               |
| 6.    | [How do you implement a `Record<K, T>` type?](#question-6-how-do-you-implement-a-recordk-t-type)                                       |
| 7.    | [How do you implement a type-safe Promise chain?](#question-7-how-do-you-implement-a-type-safe-promise-chain)                          |
| 8.    | [How do you define function overloads?](#question-8-how-do-you-define-function-overloads)                                              |
| 9.    | [How do you define an index signature with multiple types?](#question-9-how-do-you-define-an-index-signature-with-multiple-types)      |
| 10.   | [How do you define discriminated unions?](#question-10-how-do-you-define-discriminated-unions)                                         |
| 11.   | [How do you implement exhaustive checking in union types?](#question-11-how-do-you-implement-exhaustive-checking-in-union-types)       |
| 12.   | [How do you define a generic class?](#question-12-how-do-you-define-a-generic-class)                                                   |
| 13.   | [How do you implement default generic parameters in a class?](#question-13-how-do-you-implement-default-generic-parameters-in-a-class) |
| 14.   | [How do you implement polymorphic methods in a class?](#question-14-how-do-you-implement-polymorphic-methods-in-a-class)               |
| 15.   | [How do you type a Set or Map generically?](#question-15-how-do-you-type-a-set-or-map-generically)                                     |
| 16.   | [How do you define optional tuple elements?](#question-16-how-do-you-define-optional-tuple-elements)                                   |
| 17.   | [How do you define readonly tuple elements?](#question-17-how-do-you-define-readonly-tuple-elements)                                   |
| 18.   | [How do you implement type-safe destructuring of objects?](#question-18-how-do-you-implement-type-safe-destructuring-of-objects)       |
| 19.   | [How do you type a function that returns another function?](#question-19-how-do-you-type-a-function-that-returns-another-function)     |
| 20.   | [How do you type a callback with generic input/output?](#question-20-how-do-you-type-a-callback-with-generic-inputoutput)              |

## Question 1. How do you define conditional types?

## Short answer

Conditional types in TypeScript let you express types that depend on a condition using the syntax `T extends U ? X : Y`, enabling type-level branching and inference.

---

## Explanation

Conditional types are one of TypeScript’s most powerful type-level constructs. They allow you to define a type that evaluates differently based on whether a type `T` is assignable to another type `U`.

At a high level:

```ts
T extends U ? X : Y
```

- If `T` is assignable to `U`, the result is `X`
- Otherwise, the result is `Y`

### Key capabilities:

1. **Type narrowing at compile time**
   - Acts like `if/else` but for types.

2. **Distributive behavior over unions**
   - If `T` is a union, the conditional type is applied to each member.

3. **Type inference with `infer`**
   - You can extract parts of types (e.g., return types, array element types).

### Design implications:

- Enables building utility types like `ReturnType`, `Parameters`, `Exclude`, `Extract`.
- Encourages declarative, composable type systems instead of manual unions.
- Can become complex and impact type-checker performance if overused deeply.

---

## Example

```ts
type IsString<T> = T extends string ? true : false;

type A = IsString<string>; // true
type B = IsString<number>; // false

// Distributive behavior over unions
type C = IsString<string | number>;
// equivalent to IsString<string> | IsString<number>
// result: true | false
```

### With `infer` (advanced real-world pattern)

```ts
type ReturnTypeOf<T> = T extends (...args: any[]) => infer R ? R : never;

function getUser() {
  return { id: 1, name: "Alice" };
}

type User = ReturnTypeOf<typeof getUser>;
// { id: number; name: string }
```

---

## Pitfalls

- **Unintended distributive behavior**
  - Conditional types distribute over unions unless wrapped in a tuple: `[T] extends [U]`

- **Readability issues**
  - Deeply nested conditional types become hard to maintain and debug

- **Performance overhead**
  - Complex recursive conditional types can slow down type checking in large codebases

- **Overuse instead of simpler utilities**
  - Sometimes a mapped type or union is clearer

- **Inference surprises with `infer`**
  - Can produce `never` silently if pattern doesn’t match

## Question 2. How do you implement `Partial<T>` for nested objects?

## Question 3. How do you implement `Required<T>` for nested objects?

## Question 4. How do you implement `Pick<T, K>`?

## Question 5. How do you define an `Omit<T, K>` type?

## Question 6. How do you implement a `Record<K, T>` type?

## Question 7. How do you implement a type-safe Promise chain?

## Question 8. How do you define function overloads?

## Question 9. How do you define an index signature with multiple types?

## Question 10. How do you define discriminated unions?

## Question 11. How do you implement exhaustive checking in union types?

## Question 12. How do you define a generic class?

## Question 13. How do you implement default generic parameters in a class?

## Question 14. How do you implement polymorphic methods in a class?

## Question 15. How do you type a Set or Map generically?

## Question 16. How do you define optional tuple elements?

## Question 17. How do you define readonly tuple elements?

## Question 18. How do you implement type-safe destructuring of objects?

## Question 19. How do you type a function that returns another function?

## Question 20. How do you type a callback with generic input/output?
