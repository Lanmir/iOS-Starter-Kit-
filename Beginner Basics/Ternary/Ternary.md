# Ternary Operator

The **ternary operator** is a shorthand way of writing simple `if-else` statements. It allows you to evaluate a condition and return one of two values in a single line.

The syntax looks like this:

```swift
condition ? valueIfTrue : valueIfFalse
```

Think of it as:

> “If this condition is true, return this value, otherwise return that value.”

#### Basic Example

```swift
let age = 20

let canVote = age >= 18 ? true : false
print(canVote)  // true
```

This is equivalent to:

```swift
let canVote: Bool

if age >= 18 {
    canVote = true
} else {
    canVote = false
}
```
## Using with Strings

A very common use case is returning strings based on conditions.

```swift
let score = 85

let result = score >= 50 ? "Pass" : "Fail"
print(result)  // Pass
```

## Using inside Print Statements

You can directly use the ternary operator inside expressions.

```swift
let isLoggedIn = true

print(isLoggedIn ? "Welcome back!" : "Please log in")
```

## Assigning Values

The ternary operator is often used when assigning values based on a condition.

```swift
let temperature = 30
let weather = temperature > 25 ? "Hot" : "Cool"
```

## Nested Ternary Operator

You can chain ternary operators, but this can quickly become hard to read.

```swift
let marks = 75

let grade = marks >= 90 ? "A" :
            marks >= 75 ? "B" :
            marks >= 50 ? "C" : "Fail"

print(grade)  // B
```

> **Note:** Avoid overusing nested ternary operators — readability matters.

## When to Use Ternary Operator

Use it when:

-   You have a **simple condition**
-   You want to **assign a value quickly**
-   It improves **readability in one line**

Avoid it when:

-   Logic becomes complex
-   Multiple conditions are involved (use `if-else` instead)

## Ternary vs If-Else

-   **Ternary Operator** → Short, concise, single-line decisions
-   **If-Else** → Better for complex logic and readability

## Common Use Cases

-   Assigning UI labels
-   Setting colors or states
-   Simple validations
-   Quick value transformations


> **Tip**:  If you ever feel like your ternary operator is getting confusing, it probably is — switch back to `if-else`.
Clean code > clever code.