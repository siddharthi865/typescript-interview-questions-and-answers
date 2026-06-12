# Set 3

| #   | Question                                                                                                                              |
| --- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do mapped types work? Give an example](#question-1-how-do-mapped-types-work-give-an-example)                                     |
| 2   | [What is the difference between `Partial<T>` and `Required<T>` ?](#question-2-what-is-the-difference-between-partialt-and-requiredt-) |
| 3   | [Explain `Readonly<T>` and `Pick<T>` with examples](#question-3-explain-readonlyt-and-pickt-with-examples)                            |
| 4   | [Explain `Record<K, T>` type](#question-4-explain-recordk-t-type)                                                                     |
| 5   | [What are utility types in TypeScript? Give examples](#question-5-what-are-utility-types-in-typescript-give-examples)                 |
| 6   | [How do you use keyof operator?](#question-6-how-do-you-use-keyof-operator)                                                           |
| 7   | [How do you use typeof in TypeScript?](#question-7-how-do-you-use-typeof-in-typescript)                                               |
| 8   | [How do you use instanceof in TypeScript?](#question-8-how-do-you-use-instanceof-in-typescript)                                       |
| 9   | [What is type narrowing? Give examples](#question-9-what-is-type-narrowing-give-examples)                                             |
| 10  | [How do type guards work?](#question-10-how-do-type-guards-work)                                                                      |
| 11  | [What are discriminated unions?](#question-11-what-are-discriminated-unions)                                                          |
| 12  | [Explain the never type and its use cases](#question-12-explain-the-never-type-and-its-use-cases)                                     |
| 13  | [How does function overloading work in TypeScript?](#question-13-how-does-function-overloading-work-in-typescript)                    |
| 14  | [How do you define index signatures?](#question-14-how-do-you-define-index-signatures)                                                |
| 15  | [How do you handle dynamic object keys in TypeScript?](#question-15-how-do-you-handle-dynamic-object-keys-in-typescript)              |
| 16  | [What are namespaces in TypeScript?](#question-16-what-are-namespaces-in-typescript)                                                  |
| 17  | [Difference between namespaces and modules](#question-17-difference-between-namespaces-and-modules)                                   |
| 18  | [How do you handle asynchronous code in TypeScript?](#question-18-how-do-you-handle-asynchronous-code-in-typescript)                  |
| 19  | [Explain TypeScript’s Promise type](#question-19-explain-typescripts-promise-type)                                                    |
| 20  | [How do you define async/await with proper types?](#question-20-how-do-you-define-asyncawait-with-proper-types)                       |

## Question 1. How do mapped types work? Give an example

Got it — I understand the interview format and I’m ready.

---

## Short answer

Mapped types let you create new types by transforming each property of an existing type using key iteration syntax like `[K in keyof T]`.

---

## Explanation

Mapped types are a powerful TypeScript feature that enables **type-level transformations over object keys**. Instead of manually redefining types, you iterate over the keys of an existing type (`keyof T`) and generate a new type based on a transformation rule.

### Core idea

```ts
[K in keyof T]: ...
```

This means:

- Take each property key `K` from type `T`
- Produce a new property in the resulting type
- Optionally transform:
  - key (`as` clause)
  - value type
  - modifiers (`readonly`, optional `?`, etc.)

### Why it matters (senior perspective)

Mapped types enable:

- DRY type design (avoid duplication)
- Strong consistency across DTOs, API layers, and state models
- Framework-level abstractions (e.g., React props, ORM projections)
- Type-safe transformations similar to functional programming at type level

They are foundational to many built-in utility types like:

- `Partial<T>`
- `Readonly<T>`
- `Record<K, V>`
- `Pick<T, K>`

---

## Example

### Basic mapped type

```ts
type User = {
  id: number;
  name: string;
  isActive: boolean;
};

// Make all properties optional
type PartialUser = {
  [K in keyof User]?: User[K];
};

const user1: PartialUser = {
  name: "Alice",
};
```

---

### Advanced mapped type (key + value transformation)

```ts
type ApiModel<T> = {
  [K in keyof T as `api_${string & K}`]: T[K];
};

type User = {
  id: number;
  name: string;
};

type ApiUser = ApiModel<User>;

/*
Equivalent to:
{
  api_id: number;
  api_name: string;
}
*/
```

---

## Pitfalls

- Overusing mapped types can reduce readability and make debugging harder
- Complex key remapping (`as`) can break IDE autocomplete clarity
- Circular or deeply nested transformations can hurt compile performance
- Incorrect use of `keyof any` can widen types unexpectedly (losing safety)
- Mapped types don’t change runtime behavior — only compile-time safety

## Question 2. What is the difference between `Partial<T>` and `Required<T>` ?

## Question 3. Explain `Readonly<T>` and `Pick<T>` with examples

## Question 4. Explain `Record<K, T>` type

## Question 5. What are utility types in TypeScript? Give examples

## Question 6. How do you use keyof operator?

## Question 7. How do you use typeof in TypeScript?

## Question 8. How do you use instanceof in TypeScript?

## Question 9. What is type narrowing? Give examples

## Question 10. How do type guards work?

## Question 11. What are discriminated unions?

## Question 12. Explain the never type and its use cases

## Question 13. How does function overloading work in TypeScript?

## Question 14. How do you define index signatures?

## Question 15. How do you handle dynamic object keys in TypeScript?

## Question 16. What are namespaces in TypeScript?

## Question 17. Difference between namespaces and modules

## Question 18. How do you handle asynchronous code in TypeScript?

## Question 19. Explain TypeScript’s Promise type

## Question 20. How do you define async/await with proper types?
