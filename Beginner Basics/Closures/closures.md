
# Closures

A closure, like a function, contains a sequence of instructions and can take arguments and return values. However, closures don’t have names. The sequence of instructions in a closure is surrounded by curly braces `{ }`, and the `in` keyword separates the parameters and return type from the closure body.

#### Basic Syntax

```swift
{ (parameters) -> ReturnType in
    // code
}
```
#### Simple Example

```swift
let greet = {
    print("Hello!")
}

greet()  // Hello!
```
## Closures with Parameters and Return Values

```swift
let add = { (a: Int, b: Int) -> Int in
    return a + b
}

let result = add(5, 3)
print(result)  // 8
```

## Type Inference

Swift can infer parameter and return types, so you can write closures more concisely.

```swift
let add = { (a: Int, b: Int) in
    a + b
}
```

## Shorthand Argument Names

Swift provides shorthand argument names like `$0`, `$1`, etc., making closures even shorter.
```swift
let multiply: (Int, Int) -> Int = {
    $0 * $1
}

print(multiply(4, 5))  // 20
```
## Closures as Function Parameters

Closures are often passed into functions as arguments.
```swift
func performOperation(a: Int, b: Int, operation: (Int, Int) -> Int) {
    let result = operation(a, b)
    print(result)
}

performOperation(a: 10, b: 5, operation: { $0 + $1 })  // 15
```

## Trailing Closure Syntax

If a closure is the last parameter of a function, you can write it outside the parentheses.

```swift
performOperation(a: 10, b: 5) { $0 * $1 }  // 50
```

## Closures with Collections

Closures are heavily used with arrays and other collections.

```swift
let numbers = [1, 2, 3, 4, 5]

// map
let doubled = numbers.map { $0 * 2 }

// filter
let filtered = numbers.filter { $0 > 2 }

// sorted
let sorted = numbers.sorted { $0 > $1 }
```

## Capturing Values

Closures can capture and store references to variables from their surrounding context.

```swift
func makeCounter() -> () -> Int {
    var count = 0
    
    return {
        count += 1
        return count
    }
}

let counter = makeCounter()
print(counter())  // 1
print(counter())  // 2
```

## Escaping Closures

A closure is **escaping** if it is called after the function it was passed to returns.

```swift
var completionHandlers: [() -> Void] = []

func addHandler(handler: @escaping () -> Void) {
    completionHandlers.append(handler)
}
```
> Escaping closures are commonly used in networking and async operations.

## Non-Escaping Closures

Closures are non-escaping by default, meaning they are executed within the function.

```swift
func executeClosure(closure: () -> Void) {
    closure()
}
```

## Autoclosures

An `@autoclosure` automatically wraps an expression into a closure.

```swift
func logMessage(_ message: @autoclosure () -> String) {
    print(message())
}

logMessage("Hello World")
```

## Closures vs Functions

-   **Closures** → Anonymous, inline, lightweight
-   **Functions** → Named, reusable, structured

## When to Use Closures

Use closures when:

-   Passing behavior into functions
-   Working with collections (`map`, `filter`, etc.)
-   Handling async operations (callbacks)
-   Writing short, inline logic

## Common Real-world Examples

-   API callbacks (success / failure handlers)
-   Animations in UIKit / SwiftUI
-   Sorting, filtering, transforming data
-   Completion handlers

> **Note**:  Closures can look confusing at first, especially with shorthand syntax.
Start with the full syntax → then gradually shorten it.
Readability > clever one-liners.