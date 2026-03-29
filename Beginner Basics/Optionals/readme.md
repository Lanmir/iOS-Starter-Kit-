# Optionals
Optionals are used when you want to create a variable but assign a value to it later , or not assign a value to it at all, (i.e) an optional either contains a value  or does not contain a value. The process of accessing a value stored in an optional is called ***unwrapping the optional***.

So "what is an optional?", let's remember that 0 is a value too and so it exists, but an optional might have a value and exist, or may not have a value and not exist.
>Note : Let's thank Ramanujan for 0 ;)

Any data type can be optional in Swift. To make a type optional, add a question mark after it. As an example of a value that might be missing, Swift’s `Int` type has an initializer that tries to convert a `String` value into an `Int` value. However, only some strings can be converted into integers. The string `"123"` can be converted into the numeric value `123`, but the string `"hello, world"` doesn’t have a corresponding numeric value.
```swift
var age: Int? = nil // this holds nothing, so a value doesn't exist
age = 52 // now this holds a value
let possibleNumber = "123" 
let convertedNumber = Int(possibleNumber)  // The type of convertedNumber is "optional Int"
```
### Use Cases for Optionals

Optionals are particularly useful when working with data that might be absent or when dealing with external data sources (like JSON parsing) where a value might not be present. For example, when you’re retrieving data from a web service, the data might be missing or malformed, so using optionals can help handle these cases gracefully.

### Optional Binding
You use optional binding to find out whether an optional contains a value, and if so, to make that value available as a temporary constant or variable. Optional binding can be used with `if`, `guard`, and `while` statements to check for a value inside an optional.

```swift
if let actualNumber = Int(possibleNumber) {  
print("The string \"\(possibleNumber)\" has an integer value of \(actualNumber)")  
} else { 
 print("The string \"\(possibleNumber)\" couldn't be converted to an integer")
} 
 // Prints "The string "123" has an integer value of 123"
```
### Force Unwrapping

If you're certain that an optional contains a value, you can force unwrap it by adding an exclamation mark (`!`) after the optional. This extracts the value directly. However, if the optional is `nil`, force unwrapping will cause a runtime error, so it should be used with caution.
```swift
let definiteNumber: Int? = 42
print(definiteNumber!) // Force unwrapping, prints "42"
```
### Common Pitfalls with Force Unwrapping

A common mistake is force unwrapping an optional without checking if it contains a value. If the optional is `nil`, this will cause a crash at runtime. Always ensure that an optional has a value before force unwrapping it, or use optional binding instead.

### Implicitly Unwrapped Optionals

Implicitly unwrapped optionals are optionals that are automatically unwrapped whenever they are accessed, without the need for explicit unwrapping. They are declared by adding an exclamation mark (`!`) after the type instead of a question mark. Use this only when you are sure that the variable will always have a value after it's initially set.
```swift
let assumedNumber: Int! = 42
print(assumedNumber) // Automatically unwrapped, prints "42"
```
### When to Use Implicitly Unwrapped Optionals

Implicitly unwrapped optionals are best used in scenarios where a variable is nil initially but is guaranteed to have a value soon after. For example, a property that is set during initialization and is expected to never be nil afterwards.