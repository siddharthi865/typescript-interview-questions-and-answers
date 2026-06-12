# Set 5

| #   | Question                                                                                                                                              |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do recursive types work? Give an example](#question-1-how-do-recursive-types-work-give-an-example)                                               |
| 2   | [What are branded types in TypeScript?](#question-2-what-are-branded-types-in-typescript)                                                             |
| 3   | [How do you implement nominal typing in TypeScript?](#question-3-how-do-you-implement-nominal-typing-in-typescript)                                   |
| 4   | [Explain advanced keyof and indexed access types](#question-4-explain-advanced-keyof-and-indexed-access-types)                                        |
| 5   | [How do you implement type-safe event emitters?](#question-5-how-do-you-implement-type-safe-event-emitters)                                           |
| 6   | [Explain variance (covariance and contravariance) in TypeScript](#question-6-explain-variance-covariance-and-contravariance-in-typescript)            |
| 7   | [How does TypeScript handle type widening?](#question-7-how-does-typescript-handle-type-widening)                                                     |
| 8   | [How does TypeScript handle type inference with generics?](#question-8-how-does-typescript-handle-type-inference-with-generics)                       |
| 9   | [How do you create strongly-typed Redux actions in TypeScript?](#question-9-how-do-you-create-strongly-typed-redux-actions-in-typescript)             |
| 10  | [How do you handle discriminated unions in complex APIs?](#question-10-how-do-you-handle-discriminated-unions-in-complex-apis)                        |
| 11  | [How do you implement conditional props in React + TypeScript?](#question-11-how-do-you-implement-conditional-props-in-react--typescript)             |
| 12  | [How does never help with exhaustive checks in TypeScript?](#question-12-how-does-never-help-with-exhaustive-checks-in-typescript)                    |
| 13  | [How do you implement singleton patterns with TypeScript classes?](#question-13-how-do-you-implement-singleton-patterns-with-typescript-classes)      |
| 14  | [How do you extend third-party module types?](#question-14-how-do-you-extend-third-party-module-types)                                                |
| 15  | [How do you define a type-safe builder pattern in TypeScript?](#question-15-how-do-you-define-a-type-safe-builder-pattern-in-typescript)              |
| 16  | [How do you define polymorphic components in React + TypeScript?](#question-16-how-do-you-define-polymorphic-components-in-react--typescript)         |
| 17  | [How do you handle advanced keyof + mapped types for API responses?](#question-17-how-do-you-handle-advanced-keyof--mapped-types-for-api-responses)   |
| 18  | [How do you implement recursive generic types?](#question-18-how-do-you-implement-recursive-generic-types)                                            |
| 19  | [How do you define deeply nested immutable types?](#question-19-how-do-you-define-deeply-nested-immutable-types)                                      |
| 20  | [Explain best practices for maintaining a large TypeScript codebase](#question-20-explain-best-practices-for-maintaining-a-large-typescript-codebase) |

## Question 1. How do recursive types work? Give an example

## Short answer

Recursive types in TypeScript are types that reference themselves, directly or indirectly, to model nested or infinitely deep structures like trees or JSON-like data.

---

## Explanation

Recursive types allow you to define structures where a type contains itself as part of its definition. This is essential for modeling hierarchical or self-similar data such as:

- File systems (folders containing folders)
- JSON objects (objects containing nested objects/arrays)
- Linked lists and trees (nodes pointing to other nodes)

TypeScript supports recursion naturally in type aliases and interfaces, but it relies on **lazy evaluation of types** rather than runtime recursion.

### Key idea

A recursive type typically has a **base case** (non-recursive value) and a **recursive case** (self-reference).

For example:

- Base case: `string`
- Recursive case: `object containing the same type again`

Without a base case, the type would be infinitely expanding and unusable.

### Important behavior

TypeScript does **not expand recursive types infinitely at compile time**. Instead, it:

- Lazily evaluates them
- Stops expansion when a reasonable depth is reached (for tooling/diagnostics)

This makes recursive types practical for real-world deep structures.

---

## Example

### Recursive JSON-like type

```ts
type JSONValue =
  | string
  | number
  | boolean
  | null
  | JSONValue[]
  | { [key: string]: JSONValue };

const validJson: JSONValue = {
  name: "Alice",
  age: 30,
  tags: ["dev", "ts"],
  address: {
    city: "Delhi",
    coords: {
      lat: 28.61,
      lng: 77.2,
    },
  },
};
```

### Recursive tree structure

```ts
type TreeNode<T> = {
  value: T;
  children: TreeNode<T>[];
};

const tree: TreeNode<string> = {
  value: "root",
  children: [
    {
      value: "child-1",
      children: [],
    },
    {
      value: "child-2",
      children: [
        {
          value: "grandchild",
          children: [],
        },
      ],
    },
  ],
};
```

---

## Pitfalls

- **Infinite recursion without a base case** can lead to unusable or overly complex types.
- Deep recursion can cause **TypeScript performance issues** in large codebases (slow type-checking).
- Recursive types can become **hard to read and maintain**, especially when combined with generics and unions.
- Excessive nesting may trigger TypeScript’s recursion depth limits, resulting in errors like “type instantiation is excessively deep.”

## Question 2. What are branded types in TypeScript?

## Question 3. How do you implement nominal typing in TypeScript?

## Question 4. Explain advanced keyof and indexed access types

## Question 5. How do you implement type-safe event emitters?

## Question 6. Explain variance (covariance and contravariance) in TypeScript

## Question 7. How does TypeScript handle type widening?

## Question 8. How does TypeScript handle type inference with generics?

## Question 9. How do you create strongly-typed Redux actions in TypeScript?

## Question 10. How do you handle discriminated unions in complex APIs?

## Question 11. How do you implement conditional props in React + TypeScript?

## Question 12. How does never help with exhaustive checks in TypeScript?

## Question 13. How do you implement singleton patterns with TypeScript classes?

## Question 14. How do you extend third-party module types?

## Question 15. How do you define a type-safe builder pattern in TypeScript?

## Question 16. How do you define polymorphic components in React + TypeScript?

## Question 17. How do you handle advanced keyof + mapped types for API responses?

## Question 18. How do you implement recursive generic types?

## Question 19. How do you define deeply nested immutable types?

## Question 20. Explain best practices for maintaining a large TypeScript codebase
