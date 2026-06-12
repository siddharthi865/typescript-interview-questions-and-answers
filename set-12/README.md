# Set 12

| S.No. | Question                                                                                                                                               |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1.    | [How do you use `typeof` for type checking variables?](#question-1-how-do-you-use-typeof-for-type-checking-variables)                                  |
| 2.    | [How do you differentiate between `any` and `unknown`?](#question-2-how-do-you-differentiate-between-any-and-unknown)                                  |
| 3.    | [How do you use `never` to signal unreachable code?](#question-3-how-do-you-use-never-to-signal-unreachable-code)                                      |
| 4.    | [How do you import/export multiple modules from a single file?](#question-4-how-do-you-importexport-multiple-modules-from-a-single-file)               |
| 5.    | [How do you declare ambient modules with `declare module`?](#question-5-how-do-you-declare-ambient-modules-with-declare-module)                        |
| 6.    | [How do you use `esModuleInterop` with CommonJS packages?](#question-6-how-do-you-use-esmoduleinterop-with-commonjs-packages)                          |
| 7.    | [How do you type a JSON response imported in TypeScript?](#question-7-how-do-you-type-a-json-response-imported-in-typescript)                          |
| 8.    | [How do you define an array of tuples?](#question-8-how-do-you-define-an-array-of-tuples)                                                              |
| 9.    | [How do you define a function that returns multiple types?](#question-9-how-do-you-define-a-function-that-returns-multiple-types)                      |
| 10.   | [How do you define a class property with default value?](#question-10-how-do-you-define-a-class-property-with-default-value)                           |
| 11.   | [How do you declare an abstract class?](#question-11-how-do-you-declare-an-abstract-class)                                                             |
| 12.   | [How do you implement a class that extends another class?](#question-12-how-do-you-implement-a-class-that-extends-another-class)                       |
| 13.   | [How do you define a constructor with optional parameters?](#question-13-how-do-you-define-a-constructor-with-optional-parameters)                     |
| 14.   | [How do you use `super` in derived classes?](#question-14-how-do-you-use-super-in-derived-classes)                                                     |
| 15.   | [How do you define a simple enum with custom values?](#question-15-how-do-you-define-a-simple-enum-with-custom-values)                                 |
| 16.   | [How do you implement type guards for complex objects?](#question-16-how-do-you-implement-type-guards-for-complex-objects)                             |
| 17.   | [How do you create generic constraints with multiple types?](#question-17-how-do-you-create-generic-constraints-with-multiple-types)                   |
| 18.   | [How do you create a generic function with multiple type parameters?](#question-18-how-do-you-create-a-generic-function-with-multiple-type-parameters) |
| 19.   | [How do you use `extends` in generic interfaces?](#question-19-how-do-you-use-extends-in-generic-interfaces)                                           |
| 20.   | [How do you define a type for a key-value pair object?](#question-20-how-do-you-define-a-type-for-a-key-value-pair-object)                             |

## Question 1. How do you use `typeof` for type checking variables?

## Short answer

`typeof` in TypeScript lets you derive a type from a variable or value at compile time, ensuring type-safe reuse of existing runtime shapes.

---

## Explanation

In TypeScript, `typeof` is used in **type context (not runtime)** to capture the type of a variable, constant, or expression. This is different from JavaScript’s runtime `typeof` operator.

It is especially useful when:

- You want to reuse the type of an existing variable without duplicating it.
- You’re working with inferred complex types (objects, functions).
- You want to ensure consistency between a value and its type definition.

Key idea:

- `typeof` in **JavaScript** → returns a string at runtime (`"string"`, `"number"`, etc.)
- `typeof` in **TypeScript (type space)** → extracts the static type of a value

This helps avoid drift between data and type definitions and is commonly used in design systems, config objects, and API response typing.

---

## Example

```ts
const user = {
  id: 1,
  name: "Alice",
  isAdmin: false,
};

// Derive a type from the variable
type User = typeof user;

function printUser(u: User) {
  console.log(u.name.toUpperCase());
}

const newUser: User = {
  id: 2,
  name: "Bob",
  isAdmin: true,
};
```

You can also use it with functions:

```ts
function createUser(name: string) {
  return {
    id: Math.random(),
    name,
  };
}

// Extract return type
type CreateUserReturn = ReturnType<typeof createUser>;

const u: CreateUserReturn = createUser("Alice");
```

---

## Pitfalls

- Confusing runtime `typeof` with type-level `typeof` (very common interview trap).
- Overusing `typeof` can couple types tightly to implementation details.
- Changes in the source object automatically propagate, which may break consumers unexpectedly.
- Doesn’t work the same way with classes vs instances vs constructors without understanding context (`typeof Class` vs instance type).

## Question 2. How do you differentiate between `any` and `unknown`?

## Question 3. How do you use `never` to signal unreachable code?

## Question 4. How do you import/export multiple modules from a single file?

## Question 5. How do you declare ambient modules with `declare module`?

## Question 6. How do you use `esModuleInterop` with CommonJS packages?

## Question 7. How do you type a JSON response imported in TypeScript?

## Question 8. How do you define an array of tuples?

## Question 9. How do you define a function that returns multiple types?

## Question 10. How do you define a class property with default value?

## Question 11. How do you declare an abstract class?

## Question 12. How do you implement a class that extends another class?

## Question 13. How do you define a constructor with optional parameters?

## Question 14. How do you use `super` in derived classes?

## Question 15. How do you define a simple enum with custom values?

## Question 16. How do you implement type guards for complex objects?

## Question 17. How do you create generic constraints with multiple types?

## Question 18. How do you create a generic function with multiple type parameters?

## Question 19. How do you use `extends` in generic interfaces?

## Question 20. How do you define a type for a key-value pair object?
