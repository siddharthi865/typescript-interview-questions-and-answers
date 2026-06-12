# Set 20

| S.No. | Question                                                                                                                                                                             |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1.    | [How do you implement polymorphic components in React?](#question-1-how-do-you-implement-polymorphic-components-in-react)                                                            |
| 2.    | [How do you type props with conditional types?](#question-2-how-do-you-type-props-with-conditional-types)                                                                            |
| 3.    | [How do you implement type-safe plugin architectures?](#question-3-how-do-you-implement-type-safe-plugin-architectures)                                                              |
| 4.    | [How do you enforce nominal typing in TypeScript?](#question-4-how-do-you-enforce-nominal-typing-in-typescript)                                                                      |
| 5.    | [How do you implement compile-time string manipulation with template literals?](#question-5-how-do-you-implement-compile-time-string-manipulation-with-template-literals)            |
| 6.    | [How do you type deeply nested objects with optional fields?](#question-6-how-do-you-type-deeply-nested-objects-with-optional-fields)                                                |
| 7.    | [How do you implement type-safe builder patterns with generics?](#question-7-how-do-you-implement-type-safe-builder-patterns-with-generics)                                          |
| 8.    | [How do you type function pipelines generically?](#question-8-how-do-you-type-function-pipelines-generically)                                                                        |
| 9.    | [How do you type a heterogeneous array with different types at each index?](#question-9-how-do-you-type-a-heterogeneous-array-with-different-types-at-each-index)                    |
| 10.   | [How do you implement type-level validation for function parameters?](#question-10-how-do-you-implement-type-level-validation-for-function-parameters)                               |
| 11.   | [How do you implement type-safe serialization and deserialization?](#question-11-how-do-you-implement-type-safe-serialization-and-deserialization)                                   |
| 12.   | [How do you enforce type safety for third-party libraries without type definitions?](#question-12-how-do-you-enforce-type-safety-for-third-party-libraries-without-type-definitions) |
| 13.   | [How do you implement advanced conditional props in React?](#question-13-how-do-you-implement-advanced-conditional-props-in-react)                                                   |
| 14.   | [How do you type a deeply nested API response recursively?](#question-14-how-do-you-type-a-deeply-nested-api-response-recursively)                                                   |
| 15.   | [How do you implement exhaustive checks for Redux action types?](#question-15-how-do-you-implement-exhaustive-checks-for-redux-action-types)                                         |
| 16.   | [How do you implement type-safe dependency injection in TypeScript?](#question-16-how-do-you-implement-type-safe-dependency-injection-in-typescript)                                 |
| 17.   | [How do you type `Promise.all` for heterogeneous arrays?](#question-17-how-do-you-type-promiseall-for-heterogeneous-arrays)                                                          |
| 18.   | [How do you implement strongly-typed event buses in Node.js?](#question-18-how-do-you-implement-strongly-typed-event-buses-in-nodejs)                                                |
| 19.   | [How do you implement recursive mapped types?](#question-19-how-do-you-implement-recursive-mapped-types)                                                                             |
| 20.   | [How do you enforce type safety in large-scale TypeScript monorepo projects?](#question-20-how-do-you-enforce-type-safety-in-large-scale-typescript-monorepo-projects)               |

## Question 1. How do you implement polymorphic components in React?

## Short answer

Polymorphic components in React are implemented by allowing the component to change its rendered element via an `as` prop while preserving correct TypeScript typings using generic type parameters and utility types.

---

## Explanation

A polymorphic component is a design pattern where a single component can render different underlying HTML elements (e.g., `button`, `a`, `div`) depending on an `as` prop, while still preserving full type safety for props.

In TypeScript, the challenge is ensuring:

- Props of the underlying element are correctly inferred
- Custom props are merged safely
- The `ref` type matches the rendered element
- IntelliSense works correctly for consumers

### Core idea

We define a generic type parameter `C extends React.ElementType`, which represents the component or HTML tag being rendered.

We then:

1. Extract props of that element using `React.ComponentPropsWithoutRef<C>`
2. Merge with our custom props
3. Use `as` to switch rendered element
4. Preserve type inference using generics

This pattern is widely used in design systems (e.g., Chakra UI, MUI, Radix primitives).

Trade-off:

- Powerful flexibility
- Increased TypeScript complexity
- Slight runtime overhead is negligible (just prop forwarding)

---

## Example

```tsx
import React from "react";

type PolymorphicProps<C extends React.ElementType, Props = {}> = Props & {
  as?: C;
} & Omit<React.ComponentPropsWithoutRef<C>, keyof Props | "as">;

type ButtonOwnProps = {
  variant?: "primary" | "secondary";
};

type ButtonProps<C extends React.ElementType> = PolymorphicProps<
  C,
  ButtonOwnProps
>;

const Button = <C extends React.ElementType = "button">(
  props: ButtonProps<C>,
) => {
  const { as, variant, ...rest } = props;

  const Component = as || "button";

  return <Component {...rest} data-variant={variant} />;
};

// Usage examples:

const App = () => {
  return (
    <>
      <Button variant="primary">Default button</Button>

      <Button as="a" href="https://example.com">
        Link button
      </Button>

      <Button as="button" disabled>
        Native button
      </Button>
    </>
  );
};
```

---

## Pitfalls

- **Incorrect prop merging**: forgetting to omit overlapping keys can cause type conflicts or unsafe overrides.
- **Ref typing issues**: not forwarding refs correctly leads to loss of type safety for DOM access.
- **Overusing polymorphism**: too many `as` variations can make APIs harder to reason about in large design systems.
- **Runtime assumptions**: assuming all elements support same props (e.g., `href` on `div`) can lead to invalid DOM props if not properly constrained.

## Question 2. How do you type props with conditional types?

## Question 3. How do you implement type-safe plugin architectures?

## Question 4. How do you enforce nominal typing in TypeScript?

## Question 5. How do you implement compile-time string manipulation with template literals?

## Question 6. How do you type deeply nested objects with optional fields?

## Question 7. How do you implement type-safe builder patterns with generics?

## Question 8. How do you type function pipelines generically?

## Question 9. How do you type a heterogeneous array with different types at each index?

## Question 10. How do you implement type-level validation for function parameters?

## Question 11. How do you implement type-safe serialization and deserialization?

## Question 12. How do you enforce type safety for third-party libraries without type definitions?

## Question 13. How do you implement advanced conditional props in React?

## Question 14. How do you type a deeply nested API response recursively?

## Question 15. How do you implement exhaustive checks for Redux action types?

## Question 16. How do you implement type-safe dependency injection in TypeScript?

## Question 17. How do you type `Promise.all` for heterogeneous arrays?

## Question 18. How do you implement strongly-typed event buses in Node.js?

## Question 19. How do you implement recursive mapped types?

## Question 20. How do you enforce type safety in large-scale TypeScript monorepo projects?
