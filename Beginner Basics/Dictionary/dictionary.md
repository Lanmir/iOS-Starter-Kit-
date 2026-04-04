# Dictionary

 **Explanation**: Dictionaries in Swift are collections of key-value pairs, imagine a phonebook for example. Each key in a dictionary must be unique, and the keys and values can be of any data type.
 The full syntax of dictionary is `Dictionary<Key,Value>`, but generally the shorthand`[Key:Value]` is preferred and used.
- A Dictionary stores key-value pairs in an unordered list. 

|key| value |
|--|--|
|key 1| value 1|
|key 2| value 2|

>Keys must be of same type and unique , values must be of same type but not necessarily unique

- **Example**:
```swift
// Creating a dictionary
var person = ["name": "John", "age": 30, "city": "New York"] 
// Adding a new key-value pair
person["gender"] = "Male" 
// Modifying the value for an existing key
person["age"] = 31 
print(person) // Output: ["name": "John", "age": 31, "city": "New York", "gender": "Male"]
```

### Checking the number of elements in a dictionary

```swift
// Create a new dict
var contactList =["Rahul":"99","Nirmal":"100"]
// To count elements in a dict
contactList.count()//this will return 2
// To check if a dict is empty
contactList.count == 0
contactList.isEmpty 
```
### Dictionary Default Values

When accessing a value from a Swift dictionary using a key that doesn't exist, the dictionary returns `nil`. While this is often the desired behavior, you might want to provide a default value for missing keys.
```swift
let iceCreamPreferences = [
    "Alice": "Chocolate",
    "Bob": "Strawberry"
]

let aliceFlavor = iceCreamPreferences["Alice"] // "Chocolate"

let charlieFlavor = iceCreamPreferences["Charlie"] // nil

//To provide a default value, use the `default` argument:
let charlieFlavorWithDefault = iceCreamPreferences["Charlie", default: "Unknown"] // "Unknown"
```

## Dictionary Initialization

Dictionaries can be initialized in multiple ways. You can create an empty dictionary, a dictionary with key-value pairs, or use dictionary literals.
```swift
// Empty dictionary
var emptyDict: [String: Int] = [:]

// Dictionary with key-value pairs
var person: [String: Any] = ["name": "John", "age": 30, "city": "New York"]
```
### Accessing and Modifying Elements

You can access a dictionary's value using its key. You can also update, add, or remove key-value pairs using subscript syntax or built-in methods.
```swift
// Accessing a value
let name = person["name"] // Output: "John"

// Modifying a value
person["age"] = 31

// Adding a new key-value pair
person["profession"] = "Engineer"

// Removing a key-value pair
person["city"] = nil
```
### Iterating Over a Dictionary

Dictionaries store their items in an unordered list, but you can still iterate through them using a `for` loop. You can access both the keys and values as pairs.
```swift
for (key, value) in person {
    print("\(key): \(value)")
}

// Output:
// name: John
// age: 31
// profession: Engineer
```
### Common Dictionary Methods

Here are some commonly used methods and properties when working with dictionaries:
```swift
.count       // Returns the number of key-value pairs
.isEmpty     // Checks if the dictionary is empty
.keys        // Returns a collection of the dictionary’s keys
.values      // Returns a collection of the dictionary’s values
.updateValue(_:forKey:) // Updates the value for a given key
.removeValue(forKey:)   // Removes the key-value pair for a given key
```
### Merging Dictionaries

Swift provides a convenient way to merge two dictionaries using the `merge` method or the `merging` method to create a new dictionary.
```swift
var dict1 = ["a": 1, "b": 2]
let dict2 = ["b": 3, "c": 4]

dict1.merge(dict2) { (current, _) in current }
// dict1 is now ["a": 1, "b": 2, "c": 4]

let newDict = dict1.merging(dict2) { (_, new) in new }
// newDict is ["a": 1, "b": 3, "c": 4]
```
### Dictionary vs NSDictionary

Swift's `Dictionary` is type-safe and optimized for performance. In contrast, Objective-C's `NSDictionary` can store heterogeneous objects but lacks type safety. When working with Objective-C APIs, you may need to convert between `Dictionary` and `NSDictionary`.
```swift
let swiftDict: [String: Any] = ["key": "value"]
let nsDict: NSDictionary = swiftDict as NSDictionary
let backToSwift: [String: Any] = nsDict as! [String: Any]
```