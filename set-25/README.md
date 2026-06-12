# Set 25

| S.No. | Question                                                                                                                                                                                                   |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you implement polymorphic React components?](#question-1-how-do-you-implement-polymorphic-react-components)                                                                                        |
| 2.    | [How do you type React props with conditional logic?](#question-2-how-do-you-type-react-props-with-conditional-logic)                                                                                      |
| 3.    | [How do you implement type-safe plugin systems?](#question-3-how-do-you-implement-type-safe-plugin-systems)                                                                                                |
| 4.    | [How do you enforce nominal typing in TypeScript?](#question-4-how-do-you-enforce-nominal-typing-in-typescript)                                                                                            |
| 5.    | [How do you implement compile-time string transformations with template literals?](#question-5-how-do-you-implement-compile-time-string-transformations-with-template-literals)                            |
| 6.    | [How do you type deeply nested objects with optional fields recursively?](#question-6-how-do-you-type-deeply-nested-objects-with-optional-fields-recursively)                                              |
| 7.    | [How do you implement type-safe builder patterns with generics?](#question-7-how-do-you-implement-type-safe-builder-patterns-with-generics)                                                                |
| 8.    | [How do you implement generic function pipelines with type safety?](#question-8-how-do-you-implement-generic-function-pipelines-with-type-safety)                                                          |
| 9.    | [How do you type a heterogeneous array with specific types at each index?](#question-9-how-do-you-type-a-heterogeneous-array-with-specific-types-at-each-index)                                            |
| 10.   | [How do you implement type-level validation for function parameters?](#question-10-how-do-you-implement-type-level-validation-for-function-parameters)                                                     |
| 11.   | [How do you implement type-safe serialization and deserialization?](#question-11-how-do-you-implement-type-safe-serialization-and-deserialization)                                                         |
| 12.   | [How do you enforce type safety for third-party libraries without type definitions?](#question-12-how-do-you-enforce-type-safety-for-third-party-libraries-without-type-definitions)                       |
| 13.   | [How do you implement conditional props in React components?](#question-13-how-do-you-implement-conditional-props-in-react-components)                                                                     |
| 14.   | [How do you type a deeply nested API response recursively?](#question-14-how-do-you-type-a-deeply-nested-api-response-recursively)                                                                         |
| 15.   | [How do you implement exhaustive checks for Redux action types?](#question-15-how-do-you-implement-exhaustive-checks-for-redux-action-types)                                                               |
| 16.   | [How do you implement type-safe dependency injection?](#question-16-how-do-you-implement-type-safe-dependency-injection)                                                                                   |
| 17.   | [How do you type `Promise.all` for heterogeneous arrays?](#question-17-how-do-you-type-promiseall-for-heterogeneous-arrays)                                                                                |
| 18.   | [How do you implement strongly-typed event buses?](#question-18-how-do-you-implement-strongly-typed-event-buses)                                                                                           |
| 19.   | [How do you implement recursive mapped types for JSON schemas?](#question-19-how-do-you-implement-recursive-mapped-types-for-json-schemas)                                                                 |
| 20.   | [How do you enforce type safety in large-scale TypeScript monorepos with layered architecture?](#question-20-how-do-you-enforce-type-safety-in-large-scale-typescript-monorepos-with-layered-architecture) |

## Question 1. How do you implement polymorphic React components?

## Short answer

Polymorphic React components let you change the underlying rendered element (or component) via an `as` prop while preserving correct TypeScript inference for props and refs.

---

## Explanation

Polymorphic components are a TypeScript pattern used in design systems (e.g., `Box`, `Text`, `Button`) where a single component can render as different HTML tags or custom components.

For example:

- `<Box as="div" />`
- `<Box as="a" href="..." />`
- `<Box as={CustomComponent} customProp />`

The main challenge is **preserving type safety**:

- Props must change based on `as`
- Invalid props must be rejected (e.g., `href` on `div` unless `as="a"`)
- Ref typing must match the rendered element

This is typically solved using:

- Generic type parameter `T extends React.ElementType`
- `React.ComponentPropsWithoutRef<T>`
- Optional `as` prop
- Utility type merging pattern

Trade-offs:

- Increased type complexity
- Harder to debug inference issues
- Excellent API flexibility for design systems

---

## Example

```tsx
import React from "react";

type PolymorphicProps<T extends React.ElementType> = {
  as?: T;
};

type Props<T extends React.ElementType> = PolymorphicProps<T> &
  Omit<React.ComponentPropsWithoutRef<T>, keyof PolymorphicProps<T>>;

function Box<T extends React.ElementType = "div">(props: Props<T>) {
  const { as, ...rest } = props;

  const Component = as ?? "div";

  return <Component {...rest} />;
}

// Usage examples:

export default function App() {
  return (
    <>
      <Box>Default div</Box>

      <Box as="a" href="https://example.com">
        Link box
      </Box>

      <Box as="button" onClick={() => console.log("clicked")}>
        Button box
      </Box>
    </>
  );
}
```

---

## Pitfalls

- **Type explosion / slow inference**
  - Large polymorphic utilities can slow TS in large codebases.

- **Ref typing complexity**
  - Adding `forwardRef` requires additional generic constraints and can break inference if not carefully typed.

- **Prop conflicts**
  - `Omit<..., keyof PolymorphicProps>` is essential; otherwise `as` conflicts with native props.

- **Runtime mismatch risk**
  - TypeScript won't prevent invalid runtime components if `as` is dynamic or loosely typed.

## Question 2. How do you type React props with conditional logic?

## Question 3. How do you implement type-safe plugin systems?

## Question 4. How do you enforce nominal typing in TypeScript?

## Question 5. How do you implement compile-time string transformations with template literals?

## Question 6. How do you type deeply nested objects with optional fields recursively?

## Question 7. How do you implement type-safe builder patterns with generics?

## Question 8. How do you implement generic function pipelines with type safety?

## Question 9. How do you type a heterogeneous array with specific types at each index?

## Question 10. How do you implement type-level validation for function parameters?

## Question 11. How do you implement type-safe serialization and deserialization?

## Question 12. How do you enforce type safety for third-party libraries without type definitions?

## Question 13. How do you implement conditional props in React components?

## Question 14. How do you type a deeply nested API response recursively?

## Question 15. How do you implement exhaustive checks for Redux action types?

## Question 16. How do you implement type-safe dependency injection?

## Question 17. How do you type `Promise.all` for heterogeneous arrays?

## Question 18. How do you implement strongly-typed event buses?

## Question 19. How do you implement recursive mapped types for JSON schemas?

## Question 20. How do you enforce type safety in large-scale TypeScript monorepos with layered architecture?
