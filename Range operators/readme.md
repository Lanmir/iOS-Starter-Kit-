# Range Operators
Range operators allow you to represent a range of values by specifying the start and end values for a range. Swift gives us two ways of making ranges: the `..<` and `...` operators. 

The half-open range operator, `..<`, creates ranges up to but excluding the final value, and the closed range operator, `...`, creates ranges up to and _including_ the final value.
For example, the range `1..<5` contains the numbers 1, 2, 3, and 4, whereas the range `1...5` contains the numbers 1, 2, 3, 4, and 5.

```swift
for index in 1...5 { 
print("\(index) times 5 is \(index * 5)")
}
```