# Conditionals 

Usually to perform an action, we require a few conditions to be met, the same can be applied for code as we use conditionals to check for a condition and determine what action to take.
In code, such statements are called ***conditional statements***. 

There are mainly two types 
* If-Else statement *aka* If-Else ladder
* Switchcase / Switch Statement

Typically, you use the `if` statement to evaluate simple conditions with only a few possible outcomes. The `switch` statement is better suited to more complex conditions with multiple possible permutations

####  If-Else Statement
An if statement executes a block of code if a condition is true, and optionally another block of code if the condition is false, we can use it to evaluate multiple conditions at a time as well, and we use it to check not just conditions that are true but false ones as well.

```Swift
var action: String
var person = "chef"

if person == "chef" {
    action = "cook"
} else if person == "player" {
    action = "play"
} else {
    action = "limbo"
}
//Evaluating multiple conditions
var action: String
var meditation = true
var nothingInBrain = true

if meditation && nothingInBrain {
    action = "nirvana"
}
//Evaluating false conditions
if !meditation && !nothingInBrain {
    action = "distracted"
}
```

You can write the `if` statement in an _**expression form**_ as well; this is called an _**if expression**_.
```swift
// If-expression
let action = if person == "chef" {
    "cook"
} else if person == "player" {
    "play"
} else {
    "limbo"
}
```
Because the syntax for the assignment starts outside the `if` expression, there’s no need to repeat `action=` inside each branch. Instead, each branch of the `if` expression produces one of the three possible values for `action`, and the assignment uses that value.

####  Switch statement

A `switch` statement considers a value and compares it against several possible matching patterns. It then executes an appropriate block of code, based on the first pattern that matches successfully.

Imagine `switch` as an advanced form of the if-else ladder. When the conditions to check go beyond a certain number, the code for the if-else statement can become long and messy—that's where `switch` shines. 

>**Note:** Unlike `if-else`, where the `else` part is optional, `switch` is exhaustive; every possible case must be mentioned, in addition to a `default` case. 
```swift
let gtaStars = 2

switch gtaStars {
case 0:
    print("You're just starting out")

case 1:
    print("You just nabbed a lost wallet")

case 2..5:
    print("You're on the cops radar~")

default:
    print("Have you done something new?")
}
```
Just like `if-else`, there are several ways to write a `switch` statement, such as _**expression form**_, _**compound case**_, _**interval matching**_, _**tuples**_, _**value binding**_, and _**where conditionals**_. For more information, check out the official Swift documentation [here](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/controlflow/).

In contrast with `switch` statements in C and Objective-C, `switch` statements in Swift don’t fall through the bottom of each case and into the next one by default. To make one case fall into the next, use the `fallthrough` keyword.

### When to Use If-Else vs. Switch

-   **Use `if-else`** when you have a simple condition or a small number of conditions.
-   **Use `switch`** when you have multiple potential conditions, especially when those conditions can be expressed as ranges, patterns, or types.