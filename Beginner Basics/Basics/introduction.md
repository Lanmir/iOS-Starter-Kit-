# Introduction

This Repository is an attempt to systematically learn Swift/iOS development or atleast try to be a quick look-up material. 

**About Swift**: Swift is a highly readable language, it's like a mix of various programming languages like obj-c, python etc, but just the good parts.

so if you have any experience in programming you'll find the similarities, not to say that most programming languages aren't similar :)

## Getting Started

### Data Types

The basic data types
*  Int - for integers
*  Double / Float - for floating point values
*  Bool - for boolean value
*  String - for text 

```Swift
let age:Int = 21
let gpa:Float = 8.43
let gpaIsTrue:Bool = false
var name:String = "Leslee"
```
### Type Inference, Type Annotation and Type Safety
Swift automatically determines the constant or variable type based on the value you supplied.  These types can be explicitly typed or swift can understand it on it's own, this is called ***type inference***.

However, at times, you may wish to specify a type instead of letting Xcode do it for you. This is known as type ***annotation***.

Swift is a type-safe language. It checks to see whether you're assigning values of the correct type to variables and flags mismatched types as errors, this is the ***Type-Safety*** feature of Swift.

### Variables & Constants
In any programming langauge , we use something called variables to store values, and depending on actions the values stored can change.
For declaring a variable we use `var`

Similarly there's Constants, but values stored in these cannot be changed
For declaring a variable we use `let`
```swift
var explicitVar: Int = 10 // Explicitly typed variable
var implicitVar = 10      // Implicitly typed variable
let constantName =  10  // Implicitly typed constant
let explicitConstant: Int  =  10  // Explicitly typed constant
```
### Operators 
We use operators to perform any kind of operation on the data we're working on , whether it be numbers or strings.

#### Basic Operators
The basic operators used in programming is the same all across the board for any programming language 
| Operator | Function |
|--|--|
| + | Addition |
| - | Subtraction|
| * | Multiplication|
| / | Division |

> Note: The operands being used must be of similar type
#### Compound Operators
We can perform an operation and then assign the result to a variable using compound operators
| Operator | Function |
|--|--|
| += | Adds a value and assigns the result |
| -= | Subtracts a value and assigns the result |
| *= | Multiplies a value and assigns the result|
| /= | Divides a value and assigns the result |

#### Comparison Operators
These operators are used to compare one value to another and the result will be true or false
| Operator | Function |
|--|--|
| == | Equal to |
| != | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |

