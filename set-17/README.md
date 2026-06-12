# Set 17

| S.No. | Question                                                                                                                                              |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you extend an interface in TypeScript?](#question-1-how-do-you-extend-an-interface-in-typescript)                                             |
| 2.    | [How do you implement an interface in a class?](#question-2-how-do-you-implement-an-interface-in-a-class)                                             |
| 3.    | [How do you define a class with a constructor?](#question-3-how-do-you-define-a-class-with-a-constructor)                                             |
| 4.    | [How do you define private, protected, and public class members?](#question-4-how-do-you-define-private-protected-and-public-class-members)           |
| 5.    | [How do you define readonly class properties?](#question-5-how-do-you-define-readonly-class-properties)                                               |
| 6.    | [How do you implement inheritance in TypeScript?](#question-6-how-do-you-implement-inheritance-in-typescript)                                         |
| 7.    | [How do you use `super()` in a derived class?](#question-7-how-do-you-use-super-in-a-derived-class)                                                   |
| 8.    | [How do you define a generic function with one type parameter?](#question-8-how-do-you-define-a-generic-function-with-one-type-parameter)             |
| 9.    | [How do you define a generic function with multiple type parameters?](#question-9-how-do-you-define-a-generic-function-with-multiple-type-parameters) |
| 10.   | [How do you define a function type alias?](#question-10-how-do-you-define-a-function-type-alias)                                                      |
| 11.   | [How do you define an interface for a function signature?](#question-11-how-do-you-define-an-interface-for-a-function-signature)                      |
| 12.   | [How do you define an array of tuples?](#question-12-how-do-you-define-an-array-of-tuples)                                                            |
| 13.   | [How do you define a union of literal types?](#question-13-how-do-you-define-a-union-of-literal-types)                                                |
| 14.   | [How do you define an intersection of object types?](#question-14-how-do-you-define-an-intersection-of-object-types)                                  |
| 15.   | [How do you use the `typeof` operator to infer types?](#question-15-how-do-you-use-the-typeof-operator-to-infer-types)                                |
| 16.   | [How do you implement type-safe callbacks in TypeScript?](#question-16-how-do-you-implement-type-safe-callbacks-in-typescript)                        |
| 17.   | [How do you define a generic interface?](#question-17-how-do-you-define-a-generic-interface)                                                          |
| 18.   | [How do you implement generic constraints with `extends`?](#question-18-how-do-you-implement-generic-constraints-with-extends)                        |
| 19.   | [How do you define a mapped type?](#question-19-how-do-you-define-a-mapped-type)                                                                      |
| 20.   | [How do you use the `keyof` operator in mapped types?](#question-20-how-do-you-use-the-keyof-operator-in-mapped-types)                                |

## Question 1. How do you extend an interface in TypeScript?

## Short answer

You extend an interface in TypeScript using the `extends` keyword, allowing one interface to inherit properties from another and optionally add new ones.

---

## Explanation

Interface extension in TypeScript is a structural composition mechanism that enables reuse and scalability of type definitions. When you use `extends`, the child interface merges all properties from the parent interface(s), creating a new combined shape.

This is particularly useful in large codebases where domain models share common fields (e.g., `id`, `timestamps`, `auditing fields`). It promotes consistency and reduces duplication.

TypeScript also supports **multiple inheritance for interfaces**, meaning an interface can extend more than one parent. This is different from classes in JavaScript, which only support single inheritance.

Key design implications:

- Encourages composability over duplication
- Enables clean domain modeling
- Works well with structural typing (TypeScript’s core type system)
- Can be combined with declaration merging in some advanced scenarios

---

## Example

```ts
interface User {
  id: string;
  name: string;
}

interface Timestamped {
  createdAt: Date;
  updatedAt: Date;
}

// Extending a single interface
interface Admin extends User {
  permissions: string[];
}

// Extending multiple interfaces
interface AdminWithAudit extends User, Timestamped {
  permissions: string[];
  role: "admin";
}

const admin: AdminWithAudit = {
  id: "123",
  name: "Alice",
  createdAt: new Date(),
  updatedAt: new Date(),
  permissions: ["read", "write"],
  role: "admin",
};
```

---

## Pitfalls

- **Property conflicts**: If multiple extended interfaces define the same property with incompatible types, TypeScript will error.
- **Overuse can lead to deep hierarchies**: Large extension chains can reduce readability and make types harder to reason about.
- **Not the same as type intersections in all cases**: While similar to `&`, interfaces support declaration merging, which `type` aliases do not.
- **Runtime non-existence**: Interfaces are erased at compile time, so extension has no runtime effect.
- **Circular dependencies**: Complex interface extension chains can lead to maintainability issues in large projects.

## Question 2. How do you implement an interface in a class?

## Question 3. How do you define a class with a constructor?

## Question 4. How do you define private, protected, and public class members?

## Question 5. How do you define readonly class properties?

## Question 6. How do you implement inheritance in TypeScript?

## Question 7. How do you use `super()` in a derived class?

## Question 8. How do you define a generic function with one type parameter?

## Question 9. How do you define a generic function with multiple type parameters?

## Question 10. How do you define a function type alias?

## Question 11. How do you define an interface for a function signature?

## Question 12. How do you define an array of tuples?

## Question 13. How do you define a union of literal types?

## Question 14. How do you define an intersection of object types?

## Question 15. How do you use the `typeof` operator to infer types?

## Question 16. How do you implement type-safe callbacks in TypeScript?

## Question 17. How do you define a generic interface?

## Question 18. How do you implement generic constraints with `extends`?

## Question 19. How do you define a mapped type?

## Question 20. How do you use the `keyof` operator in mapped types?
