# Set 14

| S.No. | Question                                                                                                                                                        |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you define readonly tuple elements?](#question-1-how-do-you-define-readonly-tuple-elements)                                                             |
| 2.    | [How do you type a function returning a union of tuples?](#question-2-how-do-you-type-a-function-returning-a-union-of-tuples)                                   |
| 3.    | [How do you define type-safe default props in React components?](#question-3-how-do-you-define-type-safe-default-props-in-react-components)                     |
| 4.    | [How do you implement polymorphic components with generic props in React?](#question-4-how-do-you-implement-polymorphic-components-with-generic-props-in-react) |
| 5.    | [How do you define a type for React context with generics?](#question-5-how-do-you-define-a-type-for-react-context-with-generics)                               |
| 6.    | [How do you define type-safe event handlers in React?](#question-6-how-do-you-define-type-safe-event-handlers-in-react)                                         |
| 7.    | [How do you type a reducer function with discriminated action types?](#question-7-how-do-you-type-a-reducer-function-with-discriminated-action-types)           |
| 8.    | [How do you define type-safe state for useReducer?](#question-8-how-do-you-define-type-safe-state-for-usereducer)                                               |
| 9.    | [How do you define type-safe refs in React components?](#question-9-how-do-you-define-type-safe-refs-in-react-components)                                       |
| 10.   | [How do you type `useEffect` dependencies properly?](#question-10-how-do-you-type-useeffect-dependencies-properly)                                              |
| 11.   | [How do you create advanced conditional types with multiple branches?](#question-11-how-do-you-create-advanced-conditional-types-with-multiple-branches)        |
| 12.   | [How do you implement type inference with `infer` keyword?](#question-12-how-do-you-implement-type-inference-with-infer-keyword)                                |
| 13.   | [How do you define a recursive mapped type?](#question-13-how-do-you-define-a-recursive-mapped-type)                                                            |
| 14.   | [How do you implement type-level string manipulation?](#question-14-how-do-you-implement-type-level-string-manipulation)                                        |
| 15.   | [How do you implement a type-safe event emitter with generics?](#question-15-how-do-you-implement-a-type-safe-event-emitter-with-generics)                      |
| 16.   | [How do you define nominal types for strong typing?](#question-16-how-do-you-define-nominal-types-for-strong-typing)                                            |
| 17.   | [How do you implement advanced `keyof` + mapped types for API clients?](#question-17-how-do-you-implement-advanced-keyof--mapped-types-for-api-clients)         |
| 18.   | [How do you implement recursive generics for tree structures?](#question-18-how-do-you-implement-recursive-generics-for-tree-structures)                        |
| 19.   | [How do you create type-safe middleware in Express.js with TypeScript?](#question-19-how-do-you-create-type-safe-middleware-in-expressjs-with-typescript)       |
| 20.   | [How do you type GraphQL resolvers in TypeScript?](#question-20-how-do-you-type-graphql-resolvers-in-typescript)                                                |

## Question 1. How do you define readonly tuple elements?

## Short answer

You define readonly tuple elements using the `readonly` modifier before the tuple type or with `as const` for literal inference.

---

## Explanation

In TypeScript, tuples are fixed-length arrays with known element types. By default, tuple elements are mutable—you can reassign values. To enforce immutability, you use `readonly` tuples, which prevent any modification of elements, length, or structure.

There are two primary approaches:

### 1. Explicit `readonly` tuple type

You prefix the tuple type with `readonly`, which makes all elements immutable.

```ts
type Point = readonly [number, number];
```

This means:

- You cannot change `point[0]` or `point[1]`
- You cannot use mutating methods like `push`, `pop`, `splice`

### 2. `as const` assertion (literal-level immutability)

When defining values, `as const` infers the most specific literal type and makes the structure deeply readonly.

```ts
const point = [10, 20] as const;
// type is readonly [10, 20]
```

This is more powerful because:

- It preserves literal types (`10` instead of `number`)
- It enforces deep immutability

---

## Example

```ts
// Explicit readonly tuple type
type RGB = readonly [number, number, number];

const color: RGB = [255, 128, 64];

// color[0] = 0; ❌ Error: cannot assign to readonly element
// color.push(100); ❌ Error: property 'push' does not exist

// Using const assertion
const position = [100, 200] as const;

// position[0] = 0; ❌ Error
// position.push(300); ❌ Error

// Preserves literal types
type X = (typeof position)[0]; // 100 (not number)
```

---

## Pitfalls

- `readonly` only applies shallowly unless using `as const`; nested objects inside tuples may still be mutable.
- `as const` can overly narrow types (literal types) making generics harder to work with.
- Array methods that mutate (e.g., `push`, `splice`) become unavailable, which can break legacy code.
- Confusing `readonly T[]` vs `readonly [T, T]`: one is a readonly array, the other is a fixed-length tuple.

## Question 2. How do you type a function returning a union of tuples?

## Question 3. How do you define type-safe default props in React components?

## Question 4. How do you implement polymorphic components with generic props in React?

## Question 5. How do you define a type for React context with generics?

## Question 6. How do you define type-safe event handlers in React?

## Question 7. How do you type a reducer function with discriminated action types?

## Question 8. How do you define type-safe state for useReducer?

## Question 9. How do you define type-safe refs in React components?

## Question 10. How do you type `useEffect` dependencies properly?

## Question 11. How do you create advanced conditional types with multiple branches?

## Question 12. How do you implement type inference with `infer` keyword?

## Question 13. How do you define a recursive mapped type?

## Question 14. How do you implement type-level string manipulation?

## Question 15. How do you implement a type-safe event emitter with generics?

## Question 16. How do you define nominal types for strong typing?

## Question 17. How do you implement advanced `keyof` + mapped types for API clients?

## Question 18. How do you implement recursive generics for tree structures?

## Question 19. How do you create type-safe middleware in Express.js with TypeScript?

## Question 20. How do you type GraphQL resolvers in TypeScript?
