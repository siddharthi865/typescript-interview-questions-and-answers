# Set 2

| #   | Question                                                                                                                                                              |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [Difference between interface and type in TypeScript](#question-1-difference-between-interface-and-type-in-typescript)                                                |
| 2   | [How do you extend an interface?](#question-2-how-do-you-extend-an-interface)                                                                                         |
| 3   | [What is the difference between public, private, and protected in TypeScript?](#question-3-what-is-the-difference-between-public-private-and-protected-in-typescript) |
| 4   | [How do you define a class in TypeScript?](#question-4-how-do-you-define-a-class-in-typescript)                                                                       |
| 5   | [How does constructor work in TypeScript?](#question-5-how-does-constructor-work-in-typescript)                                                                       |
| 6   | [What is readonly in TypeScript?](#question-6-what-is-readonly-in-typescript)                                                                                         |
| 7   | [What is the difference between == and === in TypeScript/JavaScript?](#question-7-what-is-the-difference-between--and--in-typescriptjavascript)                       |
| 8   | [What is the difference between let, const, and var?](#question-8-what-is-the-difference-between-let-const-and-var)                                                   |
| 9   | [How do you use modules in TypeScript?](#question-9-how-do-you-use-modules-in-typescript)                                                                             |
| 10  | [What is the difference between default export and named export?](#question-10-what-is-the-difference-between-default-export-and-named-export)                        |
| 11  | [How do you import types only in TypeScript?](#question-11-how-do-you-import-types-only-in-typescript)                                                                |
| 12  | [Explain type assertion in TypeScript.](#question-12-explain-type-assertion-in-typescript)                                                                            |
| 13  | [How do you use as const in TypeScript?](#question-13-how-do-you-use-as-const-in-typescript)                                                                          |
| 14  | [What is the difference between interface and class?](#question-14-what-is-the-difference-between-interface-and-class)                                                |
| 15  | [How do you handle null and undefined in TypeScript?](#question-15-how-do-you-handle-null-and-undefined-in-typescript)                                                |
| 16  | [What are generics in TypeScript? Give an example.](#question-16-what-are-generics-in-typescript-give-an-example)                                                     |
| 17  | [How do you create a generic function?](#question-17-how-do-you-create-a-generic-function)                                                                            |
| 18  | [How do you create a generic class?](#question-18-how-do-you-create-a-generic-class)                                                                                  |
| 19  | [What is the difference between T extends U in generics?](#question-19-what-is-the-difference-between-t-extends-u-in-generics)                                        |
| 20  | [Explain conditional types in TypeScript.](#question-20-explain-conditional-types-in-typescript)                                                                      |

## Question 1. Difference between interface and type in TypeScript

Got it — I understand your interview format requirements and I’m ready for your TypeScript questions.

---

## Short answer

`interface` is best for defining object shapes with extendability, while `type` is more flexible and can represent unions, primitives, and advanced compositions.

---

## Explanation

In TypeScript, both `interface` and `type` can describe the shape of an object, and in many cases they are interchangeable. However, they differ in **capabilities, extensibility, and design intent**.

### 1. Extensibility (declaration merging vs composition)

- `interface` supports **declaration merging**, meaning multiple declarations with the same name are automatically merged.
- `type` does **not** support merging; it is a single, fixed definition.

This makes `interface` ideal for:

- Public APIs
- Library extension scenarios

### 2. Expressiveness

- `type` is more powerful because it can represent:
  - Union types
  - Intersection types
  - Primitives
  - Tuples
  - Conditional types

- `interface` is primarily for **object shapes** (though it can extend other interfaces/classes).

### 3. Tooling and readability

- `interface` is often preferred for **object-oriented design style**
- `type` is preferred for **functional and compositional modeling**

### 4. Performance (compiler behavior)

At compile time, both are similar in performance. However:

- Interfaces may enable better incremental type checking due to merging behavior
- Types may become complex faster due to advanced compositions

### 5. Design guidance (real-world usage)

- Use `interface` when:
  - Defining public object contracts
  - Expecting extension (e.g., library consumers)

- Use `type` when:
  - Using unions/intersections
  - Modeling complex transformations
  - Working with primitives or tuples

---

## Example

```ts
// Interface example (extensible)
interface User {
  id: number;
  name: string;
}

interface User {
  email?: string; // declaration merging
}

const user1: User = {
  id: 1,
  name: "Alice",
};

// Type example (more flexible)
type Admin = {
  id: number;
  role: "admin" | "superadmin";
};

type Guest = {
  sessionId: string;
};

// Union type (only possible with type)
type AppUser = Admin | Guest;

function handleUser(user: AppUser) {
  if ("role" in user) {
    console.log("Admin user:", user.role);
  } else {
    console.log("Guest session:", user.sessionId);
  }
}
```

---

## Pitfalls

- Overusing `type` for object shapes can reduce extensibility in large codebases
- Overusing `interface` can limit expressive power (no unions/intersections directly)
- Declaration merging in `interface` can cause accidental type augmentation bugs
- Complex `type` compositions can become hard to debug and read
- Mixing both inconsistently can reduce maintainability in large teams

## Question 2. How do you extend an interface?

## Question 3. What is the difference between public, private, and protected in TypeScript?

## Question 4. How do you define a class in TypeScript?

## Question 5. How does constructor work in TypeScript?

## Question 6. What is readonly in TypeScript?

## Question 7. What is the difference between == and === in TypeScript/JavaScript?

## Question 8. What is the difference between let, const, and var?

## Question 9. How do you use modules in TypeScript?

## Question 10. What is the difference between default export and named export?

## Question 11. How do you import types only in TypeScript?

## Question 12. Explain type assertion in TypeScript

## Question 13. How do you use as const in TypeScript?

## Question 14. What is the difference between interface and class?

## Question 15. How do you handle null and undefined in TypeScript?

## Question 16. What are generics in TypeScript? Give an example

## Question 17. How do you create a generic function?

## Question 18. How do you create a generic class?

## Question 19. What is the difference between T extends U in generics?

## Question 20. Explain conditional types in TypeScript
