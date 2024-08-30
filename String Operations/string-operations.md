
# String Operations
A string is a series of characters, usually denoted by the `String` type. A set of operations can be performed on strings using the appropriate method.
* Use a `+` to append a string to another string
* Append to a string by casting different types of data as string

```swift
let greeting = "Good" + "Morning" // example 1
let movieRating = 8.8
var ratingResult = "The Titanic has a rating of " + String(movieRating)//example 2
```
another simpler way is to use string interpolation
# String Interpolation
You can place any type of variable inside your string – all you have to do is write a backslash, `\`, followed by your variable name in parentheses. 
the previous example can also be called as
```swift
var ratingResult = "The Titanic has a rating of \(movieRating)"
```
>Note: you can even run code instead of just calling variables