# Set 4

| #   | Question                                                                                                                                                |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you create a tuple type with varying lengths?](#question-1-how-do-you-create-a-tuple-type-with-varying-lengths)                                 |
| 2   | [What are literal inference rules in TypeScript?](#question-2-what-are-literal-inference-rules-in-typescript)                                           |
| 3   | [How do you define a readonly array or tuple?](#question-3-how-do-you-define-a-readonly-array-or-tuple)                                                 |
| 4   | [What is symbol type and when is it used?](#question-4-what-is-symbol-type-and-when-is-it-used)                                                         |
| 5   | [How do you define custom type guards?](#question-5-how-do-you-define-custom-type-guards)                                                               |
| 6   | [How do you define a function type interface?](#question-6-how-do-you-define-a-function-type-interface)                                                 |
| 7   | [Explain structural typing in TypeScript](#question-7-explain-structural-typing-in-typescript)                                                          |
| 8   | [How do you deal with third-party JavaScript libraries in TypeScript?](#question-8-how-do-you-deal-with-third-party-javascript-libraries-in-typescript) |
| 9   | [How do you define a this type in functions?](#question-9-how-do-you-define-a-this-type-in-functions)                                                   |
| 10  | [How do you enable strict type checking and what are its benefits?](#question-10-how-do-you-enable-strict-type-checking-and-what-are-its-benefits)      |
| 11  | [Explain advanced type inference in TypeScript](#question-11-explain-advanced-type-inference-in-typescript)                                             |
| 12  | [How do you implement mixins in TypeScript?](#question-12-how-do-you-implement-mixins-in-typescript)                                                    |
| 13  | [How do decorators work in TypeScript?](#question-13-how-do-decorators-work-in-typescript)                                                              |
| 14  | [What are class decorators and method decorators?](#question-14-what-are-class-decorators-and-method-decorators)                                        |
| 15  | [How do property decorators work?](#question-15-how-do-property-decorators-work)                                                                        |
| 16  | [How do parameter decorators work?](#question-16-how-do-parameter-decorators-work)                                                                      |
| 17  | [Explain experimental decorators in TypeScript](#question-17-explain-experimental-decorators-in-typescript)                                             |
| 18  | [What are conditional mapped types?](#question-18-what-are-conditional-mapped-types)                                                                    |
| 19  | [How do you use infer in conditional types?](#question-19-how-do-you-use-infer-in-conditional-types)                                                    |
| 20  | [Explain template literal types](#question-20-explain-template-literal-types)                                                                           |

## Question 1. How do you create a tuple type with varying lengths?

## Short answer

You create tuple types with varying lengths using **variadic tuple types** (rest elements in tuple positions), e.g. `[T, ...T[]]` or more advanced spread inference with generics like `[...Head, ...Tail]`.

---

## Explanation

In TypeScript, tuples are normally fixed-length arrays with known element types per position. To allow _variable-length tuples_, TypeScript (starting in **TS 4.0**) introduced **variadic tuple types**, which let you use rest elements inside tuple definitions.

There are two common patterns:

### 1. Simple variable-length tuple (same element type repeated)

This is useful when you want at least one element, or a flexible-length list with a fixed first element.

```ts
type NonEmptyArray<T> = [T, ...T[]];
```

- First element is required
- Remaining elements (if any) must match the same type

### 2. Fully generic variadic tuples (preserving structure)

Used when you want to _capture and extend tuple shapes_ generically.

```ts
type Prepend<T extends any[], U> = [U, ...T];

type Example = Prepend<[number, boolean], string>;
// Result: [string, number, boolean]
```

### 3. Flexible tuple concatenation

You can also compose tuples dynamically:

```ts
type Concat<A extends any[], B extends any[]> = [...A, ...B];

type Result = Concat<[1, 2], [3, 4]>;
// [1, 2, 3, 4]
```

This is powerful for modeling function argument lists, pipelines, or builder patterns.

---

## Example

```ts
// Non-empty tuple of strings
type NonEmptyStringTuple = [string, ...string[]];

const a: NonEmptyStringTuple = ["hello"];
const b: NonEmptyStringTuple = ["hello", "world", "typescript"];

// Generic tuple manipulation
type Append<T extends any[], U> = [...T, U];

type T1 = Append<[number, number], string>;
// [number, number, string]

function logAll<T extends any[]>(...args: T) {
  return args;
}

const result = logAll(1, "a", true);
// inferred as [number, string, boolean]
```

---

## Pitfalls

- Variadic tuples require **TypeScript 4.0+**.
- Overusing them can make inference complex and slow in large codebases.
- Deeply nested tuple transformations may cause **type instantiation depth errors**.
- Readability suffers when tuples replace structured objects in domain models.
- Inference may degrade when spreading large or recursive tuple types.

## Question 2. What are literal inference rules in TypeScript?

## Question 3. How do you define a readonly array or tuple?

## Question 4. What is symbol type and when is it used?

## Question 5. How do you define custom type guards?

## Question 6. How do you define a function type interface?

## Question 7. Explain structural typing in TypeScript

## Question 8. How do you deal with third-party JavaScript libraries in TypeScript?

## Question 9. How do you define a this type in functions?

## Question 10. How do you enable strict type checking and what are its benefits?

## Question 11. Explain advanced type inference in TypeScript

## Question 12. How do you implement mixins in TypeScript?

## Question 13. How do decorators work in TypeScript?

## Question 14. What are class decorators and method decorators?

## Question 15. How do property decorators work?

## Question 16. How do parameter decorators work?

## Question 17. Explain experimental decorators in TypeScript

## Question 18. What are conditional mapped types?

## Question 19. How do you use infer in conditional types?

## Question 20. Explain template literal types
