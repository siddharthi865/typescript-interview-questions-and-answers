# Set 7

| S.No. | Question                                                                                                                                        |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you define a type for a callback function?](#question-1-how-do-you-define-a-type-for-a-callback-function)                               |
| 2.    | [How do you extend multiple interfaces?](#question-2-how-do-you-extend-multiple-interfaces)                                                     |
| 3.    | [How do you define a class implementing multiple interfaces?](#question-3-how-do-you-define-a-class-implementing-multiple-interfaces)           |
| 4.    | [How do you make a class property optional?](#question-4-how-do-you-make-a-class-property-optional)                                             |
| 5.    | [How do you define getters and setters in TypeScript?](#question-5-how-do-you-define-getters-and-setters-in-typescript)                         |
| 6.    | [How do you define private fields using # syntax?](#question-6-how-do-you-define-private-fields-using--syntax)                                  |
| 7.    | [What is the difference between interface and abstract class?](#question-7-what-is-the-difference-between-interface-and-abstract-class)         |
| 8.    | [How do you use TypeScript with Node.js?](#question-8-how-do-you-use-typescript-with-nodejs)                                                    |
| 9.    | [How do you use TypeScript with Express.js?](#question-9-how-do-you-use-typescript-with-expressjs)                                              |
| 10.   | [How do you define a global type in TypeScript?](#question-10-how-do-you-define-a-global-type-in-typescript)                                    |
| 11.   | [How do you define a custom module type for an npm package?](#question-11-how-do-you-define-a-custom-module-type-for-an-npm-package)            |
| 12.   | [How do you use TypeScript with Babel?](#question-12-how-do-you-use-typescript-with-babel)                                                      |
| 13.   | [How do you use comments to ignore TypeScript errors? (@ts-ignore)](#question-13-how-do-you-use-comments-to-ignore-typescript-errors-ts-ignore) |
| 14.   | [How do you use declare keyword in TypeScript?](#question-14-how-do-you-use-declare-keyword-in-typescript)                                      |
| 15.   | [How do you declare ambient types?](#question-15-how-do-you-declare-ambient-types)                                                              |
| 16.   | [What is the difference between unknown and any types?](#question-16-what-is-the-difference-between-unknown-and-any-types)                      |
| 17.   | [How do you implement a type-safe event listener?](#question-17-how-do-you-implement-a-type-safe-event-listener)                                |
| 18.   | [How do you create a type-safe API response wrapper?](#question-18-how-do-you-create-a-type-safe-api-response-wrapper)                          |
| 19.   | [How do you create a generic interface?](#question-19-how-do-you-create-a-generic-interface)                                                    |
| 20.   | [How do you create a generic type alias?](#question-20-how-do-you-create-a-generic-type-alias)                                                  |

## Question 1. How do you define a type for a callback function?

## Short answer

A callback function type in TypeScript is defined by specifying its parameter types and return type using a function type signature or a type alias.

---

## Explanation

In TypeScript, a callback is just a function passed as an argument to another function. To type it properly, you explicitly define:

- The **input parameters** the callback receives
- The **return type** it produces

There are three common ways to define callback types:

### 1. Inline function type annotation (most common for simple cases)

You directly annotate the parameter as a function type.

### 2. Type alias (best for reuse and readability)

You define a reusable function type using `type`.

### 3. Interface (useful for object-like callable contracts, less common for simple callbacks)

### Design considerations:

- Prefer **type aliases** for reusable callbacks
- Keep callback types explicit to avoid implicit `any`
- Use generics when callbacks need to be reusable across multiple data types
- Ensure return type clarity (especially for async callbacks returning `Promise<T>`)

---

## Example

```ts
// 1. Type alias for a callback
type Callback<T> = (data: T) => void;

// Function that accepts a callback
function processUser(callback: Callback<string>) {
  const userName = "Alice";
  callback(userName);
}

// Usage
processUser((name) => {
  console.log("User:", name);
});
```

### Async callback example

```ts
type AsyncCallback<T> = (data: T) => Promise<void>;

async function fetchData(callback: AsyncCallback<number>) {
  const result = 42;
  await callback(result);
}

fetchData(async (value) => {
  console.log("Received:", value);
});
```

---

## Pitfalls

- Implicit `any` in callback parameters if types aren’t defined explicitly
- Overusing inline callback types → reduces reusability
- Forgetting to type async callbacks as `Promise<T>`
- Using overly broad types like `Function` (loses type safety and IntelliSense)
- Mismatch between expected and actual callback return values causing runtime bugs

## Question 2. How do you extend multiple interfaces?

## Question 3. How do you define a class implementing multiple interfaces?

## Question 4. How do you make a class property optional?

## Question 5. How do you define getters and setters in TypeScript?

## Question 6. How do you define private fields using # syntax?

## Question 7. What is the difference between interface and abstract class?

## Question 8. How do you use TypeScript with Node.js?

## Question 9. How do you use TypeScript with Express.js?

## Question 10. How do you define a global type in TypeScript?

## Question 11. How do you define a custom module type for an npm package?

## Question 12. How do you use TypeScript with Babel?

## Question 13. How do you use comments to ignore TypeScript errors? (@ts-ignore)

## Question 14. How do you use declare keyword in TypeScript?

## Question 15. How do you declare ambient types?

## Question 16. What is the difference between unknown and any types?

## Question 17. How do you implement a type-safe event listener?

## Question 18. How do you create a type-safe API response wrapper?

## Question 19. How do you create a generic interface?

## Question 20. How do you create a generic type alias?
