# Set 8

| S.No. | Question                                                                                                                                                                                   |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1.    | [How do you restrict generic types using extends?](#question-1-how-do-you-restrict-generic-types-using-extends)                                                                            |
| 2.    | [How do you implement default type parameters in generics?](#question-2-how-do-you-implement-default-type-parameters-in-generics)                                                          |
| 3.    | [How do you define recursive types for nested structures?](#question-3-how-do-you-define-recursive-types-for-nested-structures)                                                            |
| 4.    | [How do you implement optional chaining with TypeScript?](#question-4-how-do-you-implement-optional-chaining-with-typescript)                                                              |
| 5.    | [How do you define type-safe optional parameters in functions?](#question-5-how-do-you-define-type-safe-optional-parameters-in-functions)                                                  |
| 6.    | [How do you type a function that can return multiple types?](#question-6-how-do-you-type-a-function-that-can-return-multiple-types)                                                        |
| 7.    | [How do you use conditional types with extends?](#question-7-how-do-you-use-conditional-types-with-extends)                                                                                |
| 8.    | [How do you implement discriminated unions with type?](#question-8-how-do-you-implement-discriminated-unions-with-type)                                                                    |
| 9.    | [How do you use in operator in mapped types?](#question-9-how-do-you-use-in-operator-in-mapped-types)                                                                                      |
| 10.   | [How do you use as casting in TypeScript?](#question-10-how-do-you-use-as-casting-in-typescript)                                                                                           |
| 11.   | [How do you implement readonly mapped types?](#question-11-how-do-you-implement-readonly-mapped-types)                                                                                     |
| 12.   | [How do you define index signatures with string and number?](#question-12-how-do-you-define-index-signatures-with-string-and-number)                                                       |
| 13.   | [How do you define a function type with this context?](#question-13-how-do-you-define-a-function-type-with-this-context)                                                                   |
| 14.   | [How do you use generics in class methods?](#question-14-how-do-you-use-generics-in-class-methods)                                                                                         |
| 15.   | [How do you use generics in interfaces?](#question-15-how-do-you-use-generics-in-interfaces)                                                                                               |
| 16.   | [How do you implement type-safe Promise chains?](#question-16-how-do-you-implement-type-safe-promise-chains)                                                                               |
| 17.   | [How do you define a type for a function that returns a Promise?](#question-17-how-do-you-define-a-type-for-a-function-that-returns-a-promise)                                             |
| 18.   | [How do you define a type for a function that accepts another function as a parameter?](#question-18-how-do-you-define-a-type-for-a-function-that-accepts-another-function-as-a-parameter) |
| 19.   | [How do you implement conditional property types?](#question-19-how-do-you-implement-conditional-property-types)                                                                           |
| 20.   | [How do you define a type-safe configuration object?](#question-20-how-do-you-define-a-type-safe-configuration-object)                                                                     |

## Question 1. How do you restrict generic types using extends?

## Short answer

You restrict generic types using `extends` by constraining the type parameter to a specific shape, interface, or union, ensuring only compatible types can be passed.

---

## Explanation

In TypeScript, `extends` in generics acts as a **constraint boundary**—it enforces that a generic type argument must be assignable to a specified type.

This is not inheritance in the OOP sense; instead, it’s a **type compatibility filter**.

### Why it matters

- Ensures type safety at compile time
- Enables safe property access inside generic functions
- Improves API expressiveness (you can assume certain structure exists)
- Prevents overly permissive generics like `any`

### Design implications

- Tight constraints improve safety but reduce flexibility
- Loose constraints increase reuse but push checks to runtime or callers
- Good API design balances expressiveness and strictness

---

## Example

```ts
type HasId = {
  id: string;
};

function getById<T extends HasId>(items: T[], id: string): T | undefined {
  return items.find((item) => item.id === id);
}

// Valid
const users = [
  { id: "1", name: "Alice" },
  { id: "2", name: "Bob" },
];

const user = getById(users, "1");

// Invalid: missing `id`
// getById([{ name: "NoId" }], "1"); // ❌ Type error
```

Here, `T extends HasId` guarantees every `T` has an `id`, allowing safe access inside the function.

---

## Pitfalls

- Over-constraining generics reduces reusability (forces unnecessary properties)
- Confusing `extends` constraint with class inheritance semantics
- Forgetting constraints leads to unsafe property access (`T` may not have required fields)
- Using overly broad constraints like `extends object` provides little value

## Question 2. How do you implement default type parameters in generics?

## Question 3. How do you define recursive types for nested structures?

## Question 4. How do you implement optional chaining with TypeScript?

## Question 5. How do you define type-safe optional parameters in functions?

## Question 6. How do you type a function that can return multiple types?

## Question 7. How do you use conditional types with extends?

## Question 8. How do you implement discriminated unions with type?

## Question 9. How do you use in operator in mapped types?

## Question 10. How do you use as casting in TypeScript?

## Question 11. How do you implement readonly mapped types?

## Question 12. How do you define index signatures with string and number?

## Question 13. How do you define a function type with this context?

## Question 14. How do you use generics in class methods?

## Question 15. How do you use generics in interfaces?

## Question 16. How do you implement type-safe Promise chains?

## Question 17. How do you define a type for a function that returns a Promise?

## Question 18. How do you define a type for a function that accepts another function as a parameter?

## Question 19. How do you implement conditional property types?

## Question 20. How do you define a type-safe configuration object?
