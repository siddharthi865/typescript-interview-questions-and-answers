# Set 10

| S.No. | Question                                                                                                                                                                                                 |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you implement nominal typing in TypeScript?](#question-1-how-do-you-implement-nominal-typing-in-typescript)                                                                                      |
| 2.    | [How do you extend existing module types with declaration merging?](#question-2-how-do-you-extend-existing-module-types-with-declaration-merging)                                                        |
| 3.    | [How do you implement type-safe event emitters in Node.js?](#question-3-how-do-you-implement-type-safe-event-emitters-in-nodejs)                                                                         |
| 4.    | [How do you type a recursive component structure in React?](#question-4-how-do-you-type-a-recursive-component-structure-in-react)                                                                        |
| 5.    | [How do you define deeply nested optional types?](#question-5-how-do-you-define-deeply-nested-optional-types)                                                                                            |
| 6.    | [How do you implement type-safe form validation?](#question-6-how-do-you-implement-type-safe-form-validation)                                                                                            |
| 7.    | [How do you type complex API response structures?](#question-7-how-do-you-type-complex-api-response-structures)                                                                                          |
| 8.    | [How do you implement advanced `keyof` mapped types?](#question-8-how-do-you-implement-advanced-keyof-mapped-types)                                                                                      |
| 9.    | [How do you implement type-safe function pipelines?](#question-9-how-do-you-implement-type-safe-function-pipelines)                                                                                      |
| 10.   | [How do you type a union of object types with shared properties?](#question-10-how-do-you-type-a-union-of-object-types-with-shared-properties)                                                           |
| 11.   | [How do you use the `infer` keyword in conditional types?](#question-11-how-do-you-use-the-infer-keyword-in-conditional-types)                                                                           |
| 12.   | [How do you implement type-safe middleware in Express.js?](#question-12-how-do-you-implement-type-safe-middleware-in-expressjs)                                                                          |
| 13.   | [How do you implement generic constraints across multiple types?](#question-13-how-do-you-implement-generic-constraints-across-multiple-types)                                                           |
| 14.   | [How do you enforce type safety in large-scale TypeScript projects with layered architecture?](#question-14-how-do-you-enforce-type-safety-in-large-scale-typescript-projects-with-layered-architecture) |
| 15.   | [How do you implement type-safe logging utilities?](#question-15-how-do-you-implement-type-safe-logging-utilities)                                                                                       |
| 16.   | [How do you define polymorphic class hierarchies with generics?](#question-16-how-do-you-define-polymorphic-class-hierarchies-with-generics)                                                             |
| 17.   | [How do you implement compile-time string transformations with template literal types?](#question-17-how-do-you-implement-compile-time-string-transformations-with-template-literal-types)               |
| 18.   | [How do you implement type-safe plugin systems?](#question-18-how-do-you-implement-type-safe-plugin-systems)                                                                                             |
| 19.   | [How do you handle type-level recursion in TypeScript?](#question-19-how-do-you-handle-type-level-recursion-in-typescript)                                                                               |
| 20.   | [How do you type Promise.all and Promise.race for multiple types?](#question-20-how-do-you-type-promiseall-and-promiserace-for-multiple-types)                                                           |

## Question 1. How do you implement nominal typing in TypeScript?

## Short answer

TypeScript is structurally typed, but you can simulate nominal typing using **branded (opaque) types** with unique symbols or tagged properties to prevent accidental type compatibility.

---

## Explanation

TypeScript normally uses **structural typing**, meaning two types are compatible if their shapes match. This is flexible but can be unsafe for domain modeling (e.g., mixing `UserId` and `OrderId` if both are just `string`).

To enforce **nominal typing**, we “brand” a type with a unique identifier that makes it incompatible with other structurally identical types.

There are two common approaches:

### 1. Branded types (most common, lightweight)

We intersect a base type with a unique marker property:

```ts
declare const brand: unique symbol;

type Brand<T, TBrand> = T & { readonly [brand]: TBrand };

type UserId = Brand<string, "UserId">;
type OrderId = Brand<string, "OrderId">;
```

Now even though both are strings, they are not assignable to each other.

### 2. Opaque types via helper functions (safer at runtime boundaries)

We prevent accidental creation of branded values by requiring constructors:

---

## Example

```ts
declare const brand: unique symbol;

type Brand<T, TBrand> = T & { readonly [brand]: TBrand };

type UserId = Brand<string, "UserId">;
type OrderId = Brand<string, "OrderId">;

// helper constructors
const UserId = (id: string): UserId => id as UserId;
const OrderId = (id: string): OrderId => id as OrderId;

function getUser(id: UserId) {
  return `User: ${id}`;
}

const u = UserId("123");
const o = OrderId("123");

getUser(u); // OK
// getUser(o); ❌ Error: OrderId not assignable to UserId
// getUser("123"); ❌ Error
```

---

## Pitfalls

- **Type safety is compile-time only**: runtime values are still plain strings.
- **Casting (`as`) can bypass safety**, so constructors should be controlled.
- **Overuse can reduce ergonomics**, especially in large public APIs.
- **Serialization/deserialization loses branding**, requiring re-validation when parsing external data.
- Debugging can be harder because branded types don’t appear differently at runtime.

## Question 2. How do you extend existing module types with declaration merging?

## Question 3. How do you implement type-safe event emitters in Node.js?

## Question 4. How do you type a recursive component structure in React?

## Question 5. How do you define deeply nested optional types?

## Question 6. How do you implement type-safe form validation?

## Question 7. How do you type complex API response structures?

## Question 8. How do you implement advanced `keyof` mapped types?

## Question 9. How do you implement type-safe function pipelines?

## Question 10. How do you type a union of object types with shared properties?

## Question 11. How do you use the `infer` keyword in conditional types?

## Question 12. How do you implement type-safe middleware in Express.js?

## Question 13. How do you implement generic constraints across multiple types?

## Question 14. How do you enforce type safety in large-scale TypeScript projects with layered architecture?

## Question 15. How do you implement type-safe logging utilities?

## Question 16. How do you define polymorphic class hierarchies with generics?

## Question 17. How do you implement compile-time string transformations with template literal types?

## Question 18. How do you implement type-safe plugin systems?

## Question 19. How do you handle type-level recursion in TypeScript?

## Question 20. How do you type Promise.all and Promise.race for multiple types?
