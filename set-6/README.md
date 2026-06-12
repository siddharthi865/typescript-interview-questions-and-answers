# Set 6

| S.No. | Question                                                                                                                                                                                        |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | [How do you enable strict null checks in TypeScript?](#question-1-how-do-you-enable-strict-null-checks-in-typescript)                                                                           |
| 2.    | [What is the difference between null and undefined in TypeScript?](#question-2-what-is-the-difference-between-null-and-undefined-in-typescript)                                                 |
| 3.    | [How do you define an optional property in an interface?](#question-3-how-do-you-define-an-optional-property-in-an-interface)                                                                   |
| 4.    | [How do you define a readonly property in an interface?](#question-4-how-do-you-define-a-readonly-property-in-an-interface)                                                                     |
| 5.    | [What are tuple types with optional elements?](#question-5-what-are-tuple-types-with-optional-elements)                                                                                         |
| 6.    | [How do you use type unions with arrays?](#question-6-how-do-you-use-type-unions-with-arrays)                                                                                                   |
| 7.    | [Explain the difference between interface merging and type merging](#question-7-explain-the-difference-between-interface-merging-and-type-merging)                                              |
| 8.    | [How do you use default generic types?](#question-8-how-do-you-use-default-generic-types)                                                                                                       |
| 9.    | [How do you define a function that takes a variable number of arguments (rest parameters)?](#question-9-how-do-you-define-a-function-that-takes-a-variable-number-of-arguments-rest-parameters) |
| 10.   | [What are type predicates and how are they used?](#question-10-what-are-type-predicates-and-how-are-they-used)                                                                                  |
| 11.   | [How do you define void functions in TypeScript?](#question-11-how-do-you-define-void-functions-in-typescript)                                                                                  |
| 12.   | [How do you specify a function return type that never returns?](#question-12-how-do-you-specify-a-function-return-type-that-never-returns)                                                      |
| 13.   | [What is the difference between object and {} types?](#question-13-what-is-the-difference-between-object-and--types)                                                                            |
| 14.   | [How do you define a map/dictionary in TypeScript?](#question-14-how-do-you-define-a-mapdictionary-in-typescript)                                                                               |
| 15.   | [How do you define nested object types?](#question-15-how-do-you-define-nested-object-types)                                                                                                    |
| 16.   | [How do you import JSON files in TypeScript?](#question-16-how-do-you-import-json-files-in-typescript)                                                                                          |
| 17.   | [How do you use esModuleInterop in TypeScript?](#question-17-how-do-you-use-esmoduleinterop-in-typescript)                                                                                      |
| 18.   | [What is the difference between import \* as and import {}?](#question-18-what-is-the-difference-between-import--as-and-import-)                                                                |
| 19.   | [How do you define type-safe constants in TypeScript?](#question-19-how-do-you-define-type-safe-constants-in-typescript)                                                                        |
| 20.   | [How do you use string enums vs numeric enums?](#question-20-how-do-you-use-string-enums-vs-numeric-enums)                                                                                      |

## Question 1. How do you enable strict null checks in TypeScript?

## Short answer

Enable strict null checks by setting `"strictNullChecks": true` in `tsconfig.json`, or more commonly, by enabling `"strict": true`, which includes it automatically.

---

## Explanation

TypeScript’s null safety system is opt-in. Without `strictNullChecks`, `null` and `undefined` are assignable to all types, which defeats much of the type safety.

When `strictNullChecks` is enabled:

- `null` and `undefined` become distinct types.
- You must explicitly allow them via unions (e.g., `string | null`).
- The compiler forces you to handle potentially missing values via narrowing, guards, or optional chaining.

In modern TypeScript (recommended), teams typically enable `"strict": true` because it bundles multiple safety checks:

- `strictNullChecks`
- `noImplicitAny`
- `strictFunctionTypes`
- `strictBindCallApply`
- `strictPropertyInitialization`
- `useUnknownInCatchVariables`

This leads to safer code and fewer runtime `Cannot read property of undefined` errors.

Trade-off:

- More upfront type work (handling `undefined` explicitly)
- Significantly fewer runtime bugs in large codebases

---

## Example

### tsconfig.json

```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

Or explicitly:

```json
{
  "compilerOptions": {
    "strictNullChecks": true
  }
}
```

---

### TypeScript example (strict mode)

```ts
type User = {
  name: string;
  email?: string; // optional = string | undefined
};

function getEmail(user: User): string {
  // ❌ Error in strict mode: Object is possibly 'undefined'
  // return user.email.toLowerCase();

  // ✅ Safe narrowing
  if (!user.email) {
    return "no-email@example.com";
  }

  return user.email.toLowerCase();
}

const u: User = { name: "Alice" };
console.log(getEmail(u));
```

---

## Pitfalls

- Assuming `undefined` is still “ignored” leads to compilation errors after enabling strict mode.
- Overusing non-null assertions (`!`) can reintroduce runtime crashes.
- Legacy codebases may require incremental adoption (`strictNullChecks` first, then full `strict`).
- External JS libraries may need type fixes or `undefined` handling wrappers.

## Question 2. What is the difference between null and undefined in TypeScript?

## Question 3. How do you define an optional property in an interface?

## Question 4. How do you define a readonly property in an interface?

## Question 5. What are tuple types with optional elements?

## Question 6. How do you use type unions with arrays?

## Question 7. Explain the difference between interface merging and type merging

## Question 8. How do you use default generic types?

## Question 9. How do you define a function that takes a variable number of arguments (rest parameters)?

## Question 10. What are type predicates and how are they used?

## Question 11. How do you define void functions in TypeScript?

## Question 12. How do you specify a function return type that never returns?

## Question 13. What is the difference between object and {} types?

## Question 14. How do you define a map/dictionary in TypeScript?

## Question 15. How do you define nested object types?

## Question 16. How do you import JSON files in TypeScript?

## Question 17. How do you use esModuleInterop in TypeScript?

## Question 18. What is the difference between import \* as and import {}?

## Question 19. How do you define type-safe constants in TypeScript?

## Question 20. How do you use string enums vs numeric enums?
