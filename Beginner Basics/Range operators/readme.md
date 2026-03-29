# Range Operators
Range operators allow you to represent a range of values by specifying the start and end values for a range. Swift gives us two ways of making ranges: the `..<` and `...` operators. 

## Half-open & Closed range
The half-open range operator, `..<`, creates ranges up to but excluding the final value, and the closed range operator, `...`, creates ranges up to and _including_ the final value.
For example, the range `1..<5` contains the numbers 1, 2, 3, and 4, whereas the range `1...5` contains the numbers 1, 2, 3, 4, and 5.

The *half-open range* is especially useful when working with  **zero-based indexing** (as in arrays), whereas The *closed range* is more intuitive when you need to include the upper boundary.

```swift
//closed range
for index in 1...5 { 
	print("\(index) times 5 is \(index * 5)")
}

// half-open range
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count  
for i in 0..<count {  
	print("Person \(i + 1) is called \(names[i])")  
}
```
## One-sided range
The closed range operator has an alternative form for ranges that continue as far as possible in one direction, you can omit the value from one side of the range operator. This kind of range is called a _one-sided range_ because the operator has a value on only one side.

```swift
//one-sided range
for name in names[2...] {  
	print(name)  
}
for name in names[...2] {
    print(name)  
}
for name in names[..<2] {  
	print(name)  
}
```