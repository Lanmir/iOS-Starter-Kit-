# Functions

Functions let us re-use code, which means we can write a function to do something interesting then run that function from lots of places. Repeating code is generally a bad idea, and functions help us avoid doing that.

Every function has a descriptive name. You can define one or more values that the function takes as input, known as `parameters`, the value you provide to parameters are called as `arguments`. You can also define what the function will output when done, known as its `return type`.

>Note: Both parameters and return types are optional.

This is what a function call looks like:`functionName(parameter1: argument1, …)` and this is called as a `function signature`.

```swift
func greet(person: String) -> String {
	let greeting = "Hello, " + person + "!"
	return greeting
}
```
## Parameters and Return Types

-   **Single Parameter**: Functions can take parameters and return values.
-   **Multiple Parameters**: Functions can have multiple parameters of varying types.
-   **No Return Value**: If a function does not return a value, it has a return type of `Void` or `()`.

## External and internal parameter names

Sometimes you want parameters to be named one way when a function is called, but another way inside the function itself. This means that when you call a function it uses almost natural English, but inside the function the parameters have sensible names.
```swift
func countLetters(string: String) {
	print("The string \(string) has \(string.count) letters.")
}
countLetters(string: "Hello") // using the parameter name

func add(firstNumber: Int, to secondNumber: Int) -> Int{
	return firstNumber + secondNumber
}
add(firstNumber:15, to: 20) // 35
add(15 ,to: 20) //35, this initializer is valid if you add an _ as argument label
```
## Default Parameter Values

You can assign default values to parameters, allowing the function to be called with fewer arguments. You can also pass your own value instead of the default value.
```swift
func greet(person: String, withGreeting greeting: String = "Hello") {
    print("\(greeting), \(person)!")
}
greet(person: "Alice") // Output: "Hello, Alice!"
greet(person: "Mrinal", withGreeting: "Good day") // "Good day, Mrinal!"
```
## Variadic Parameters
Some functions are _`variadic`_, which is a way of saying they accept any number of parameters of the same type. You can make any parameter variadic by writing `...` after its type.
```swift
print("Haters","gonna","hate") // Haters gonna hate
func square(num:Int...){
 for n in num{
	print("\(n) squared is \(n * n)")
  }
}
square(num: 1, 2, 3) // 1 squared is 1 
// 2 squared is 4
// 3 squared is 9
```
>Fun fact: the print function is variadic. so they'll print on the same line with a space.

## In-Out Parameters
All parameters passed into a Swift function are _constants_, so you can’t change them, if you try to , it'll result in a compile time error. If you want, you can pass in one or more parameters as `inout`, which means they can be changed inside your function, and those changes reflect in the original value outside the function.
You place an ampersand (`&`) directly before a variable’s name when you pass it as an argument to an in-out parameter, to indicate that it can be modified by the function.

>Note: In-out parameters can’t have default values, and variadic parameters can’t be marked as `inout`.
```swift
func swapValues(_ a: inout Int, _ b: inout Int) {
    let temp = a
    a = b
    b = temp
}
var x = 4
var y = 99
print("x is \(x), y is \(y)") // x is 4, y is 99
swapValues(&x, &y)
print("x is \(x), y is \(y)") // x is 99, y is 4

```
>Note: In-out parameters aren’t the same as returning a value from a function. In-out parameters are an alternative way for a function to have an effect outside of the scope of its function body.

## Returning Multiple Values with Tuples
You can use a tuple type as the return type for a function to return multiple values as part of one compound return value.

```swift
func calculateAreaAndPerimeter(length: Double, width: Double) -> (area: Double, perimeter: Double) {
    let area = length * width
    let perimeter = 2 * (length + width)
    return (area, perimeter)
}

// Example usage:
let rectangleDimensions = (length: 5.0, width: 3.0)
let (area, perimeter) = calculateAreaAndPerimeter(length: rectangleDimensions.length, width: rectangleDimensions.width)

print("Area: \(area)")
print("Perimeter: \(perimeter)")
```
## Throwing functions
Sometimes functions fail because they have bad input, or because something went wrong internally. Swift lets us throw errors from functions by marking them as `throws` before their return type, then using the `throw` keyword when something goes wrong. Throwing functions allow you to handle potential errors in a more structured and controlled way.
```swift
enum DivisionError: Error {
    case divisionByZero
}

func divide(dividend: Int, divisor: Int) throws -> Int {
    if divisor == 0 {
        throw DivisionError.divisionByZero
    }
    return dividend / divisor
}

func calculateResult() {
    do {
        let result = try divide(dividend: 10, divisor: 2)
        print("Result: \(result)")
    } catch DivisionError.divisionByZero {
        print("Error: Division by zero")
    } catch {
        print("An unexpected error occurred")
    }
}

calculateResult()
```
## Nested Functions 
Nested functions are functions defined within another function. They can be useful for creating helper functions that are only needed within a specific scope, improving code organization and readability.

```swift
func factorial(number: Int) -> Int {
    func factorialHelper(number: Int) -> Int {
        if number == 0 {
            return 1
        } else {
            return number * factorialHelper(number: number - 1)
        }
    }
    
    return factorialHelper(number: number)
}

let result = factorial(number: 5)
print(result) // Output: 120
```
## Using Function Types
Every function has a specific  _function type_, made up of the parameter types and the return type of the function. You use function types just like any other types in Swift. For example, you can define a constant or variable to be of a function type and assign an appropriate function to that variable
```swift
func addTwoInts(_ a: Int, _ b: Int) -> Int {
  return a + b  
}
var mathFunction: (Int, Int) -> Int  = addTwoInts
print("Result: \(mathFunction(2, 3))")  // Prints "Result: 5"
```
### Functions as Return Types
A function can return another function as its return type.
```swift
func makePi() -> (() -> Double){
	func generatePi() -> Double{
		return 22.0/7.0
	}
	return generatePi
}
let pi = makePi()
print(pi())
```
### Functions as Parameters
A function can take another function as parameter.
```swift
func printMathResult(_ mathFunction: (Int, Int) -> Int, _ a: Int, _ b: Int) {
  print("Result: \(mathFunction(a, b))")  
 }  
 printMathResult(addTwoInts, 3, 5)  // Prints "Result: 8"
```