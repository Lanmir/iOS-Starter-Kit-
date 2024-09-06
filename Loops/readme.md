# Loops
In programming, you frequently need to the same thing over and over again, and loops are used for this.
There are 3 types of loops
* For-in loop
* while loop
* repeat-while loop
The for-in loop will repeat for a known number of times, and the while and repeat-while will repeat as long as the loop condition is true.

### For-in 
You use the `for`-`in` loop to iterate over a sequence, such as items in an array, ranges of numbers, or characters in a string.
```swift
let count = 1...10

for number in count {
    print("Number is \(number)")
}
for _ in count { // we can use an underscore instead of creating a temporary var
    print("Number is \(number)")
}
```
### While
A `while` loop starts by evaluating a single condition. If the condition is `true`, a set of statements is repeated until the condition becomes `false`.

```swift
var number = 1
while number <= 20 {
    print(number)
    number += 1   // Ensure to modify the variable to avoid infinite loops
}
print("Ready or not, here I come!")
```
### Repeat-while

The other variation of the `while` loop, known as the `repeat`-`while` loop, performs a single pass through the loop block first, _before_ considering the loop’s condition. It then continues to repeat the loop until the condition is `false`.
>Note: Also known as do-while in other languages.
```swift
var number = 1
repeat {
    print(number)
    number += 1   // This loop always runs at least once
} while number <= 20
print("Ready or not, here I come!")
```