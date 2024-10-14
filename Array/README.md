# Arrays
## Array
An `array` stores values of the same type in an ordered list. The same value can appear in an array multiple times at different positions. The full array syntax is `Array<Element>`., but generally the shorthand `[Element]` is preferred and used. 


Here's how it would look

|Index|Value|
|-----|-----|
|0|Value 1|
|1|Value 2|

In code it would look like this

```Swift
//There are two ways to declare an array.
//Specifying the type of array
let shoppingList: [String] = ["Eggs","Milk"]
//Not Specifying the type of array
let shoppingList = ["Eggs","Milk"]
```
## Array initialization
Since arrays are used to store collections of data, it’s a good practice to initialize them with the type of data they will store. We can do this by creating an empty array or an array with placeholder data.

There are 2 ways to initialize an array in swift, using `Array(repeating:count:)` or creating an empty array.

Using `Array(repeating:count:)`we can create an array with a specified number of elements as placeholder values

```swift
//creates an array like [0.0, 0.0, 0.0]
var test = Array(repeating: 0.0, count: 3)

//creates an empty array
var emptyArray: [String] = []

// You can initialize a 2D array of 3X3 like this
let matrix = Array(repeating:Array(repeating:0.0, count: 3), count: 3)
/* Output would be like this
[
	[0.0, 0.0, 0.0],
	[0.0, 0.0, 0.0],
	[0.0, 0.0, 0.0]
]
*/
```
### Accessing and Modifying Elements

You access and modify an array through its methods and properties, or by using subscript syntax. We can access elements in an array via indices as well.
```swift
var numbers = [10, 20, 30, 40]
let firstElement = numbers[0]  // Access the first element
numbers[0] = 100               // Modify the first element
```
### Array Properties and Methods
Arrays come with built-in properties and methods that allow you to manipulate and query their contents efficiently, let's see a few commonly used ones.
```swift
.count // - Getting the number of elements.
.isEmpty // - Checking if the array is empty.
.append // - Adding elements to the end.
.insert(_: at: ): // - Inserting elements at specific positions.
.remove(at: ) and .removeLast(): // -Removing elements
.contains(): // -Checking for specific elements
//to get first item
let firstItem = shoppingList.first  // Optional("Eggs")
//to get last item
let lastItem = shoppingList.last    // Optional("Milk")

```
### Iterating over Arrays
You can iterate over an array using a `for` loop, which lets you access each element in sequence. You can also use the `.enumerated()` method if you need both the index and the value of each element.

```swift
//Basic iteration:
let shoppingList = ["Eggs", "Milk", "Bread"]
for item in shoppingList { print(item) }
// Output: Eggs Milk Bread

//Iterating with index:
for (index, item) in shoppingList.enumerated() {
    print("Item \(index + 1): \(item)")
}
// Output: 
// Item 1: Eggs
// Item 2: Milk
// Item 3: Bread
```
### Multi-dimensional Arrays
Arrays in Swift can also store arrays, creating multi-dimensional arrays. This is useful when dealing with grids, matrices, or tables of data.

Example of a 2D array (like a matrix):
```swift
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print(matrix[1][1])  // Output: 5
```
### Array Slicing and Ranges
Swift arrays support slicing, which allows you to create a subarray from an existing array using a range of indices.
```swift
let numbers = [10, 20, 30, 40, 50]
let slice = numbers[1...3]
print(slice)  // Output: [20, 30, 40]
// Using half-open ranges
let slice = numbers[..<3] // Output: [10, 20, 30]
```
### Common Array Operations
A few common operations you might use with arrays:
* Sorting
* Reversing
* Filtering
* Mapping
```swift
let sortedArray = numbers.sorted()
// Sorts the array in ascending order
let reversedArray = numbers.reversed()
let filteredArray = numbers.filter { $0 > 20 }
// Filters out elements less than or equal to 20
let mappedArray = numbers.map { $0 * 2 }
// Doubles each element in the array
```
### Array vs NSArray
Swift's `Array` and Objective-C's `NSArray` have some differences. Swift's `Array` is type-safe and can contain only elements of the same type, while `NSArray` can store heterogeneous objects.

If you're working with Objective-C APIs, you might need to convert between `Array` and `NSArray`.
```swift
//example of bridging
let swiftArray: [String] = ["Hello", "World"]
let nsArray: NSArray = swiftArray as NSArray
let backToSwift: [String] = nsArray as! [String]
```