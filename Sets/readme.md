# Sets

## What is a Set?

A `set` is an unordered collection of unique values. In Swift, sets ensure that each element only appears once, and unlike arrays, sets do not maintain any specific order.

The syntax for a set is `Set<Element>` where `Element` represents the type of values the set will hold.

### Set vs Array

-   **Uniqueness**: Sets only store unique elements, while arrays can have duplicates.
-   **Order**: Sets don’t preserve the order of elements, whereas arrays maintain the order in which elements are added.

## Creating and Initializing Sets

Sets can be created from arrays or directly initialized with elements.

### Creating an empty set:
```swift
var letters = Set<Character>()  // Empty set of Character type
```
### Creating a set with initial values:
```swift
var favoriteGenres: Set<String> = ["Rock", "Classical", "Jazz"]
```
Swift can infer the type, so you can omit the type annotation.
```swift
var favoriteGenres: Set = ["Rock", "Classical", "Jazz"]
```
## Accessing and Modifying a Set

Like arrays, sets provide methods to add, remove, and check elements.

### Inserting and Removing Elements:
```swift
favoriteGenres.insert("Pop")
favoriteGenres.remove("Jazz")
```
### Checking for Existence:
```swift
if favoriteGenres.contains("Rock") {
    print("Rock is in the set")
}
```
## Set Operations

Sets in Swift offer a range of powerful operations for comparing and combining sets.

### Fundamental Set Operations:

-   **Union**: Combines all elements from two sets.
-   **Intersection**: Returns only elements common to both sets.
-   **Subtraction**: Returns elements in one set that aren’t in another.
-   **Symmetric Difference**: Returns elements that are in one set or the other, but not both.

```swift
let oddNumbers: Set = [1, 3, 5, 7]
let evenNumbers: Set = [2, 4, 6, 8]
let primeNumbers: Set = [2, 3, 5, 7]

// Union
let unionSet = oddNumbers.union(evenNumbers)  // [1, 2, 3, 4, 5, 6, 7, 8]

// Intersection
let intersectionSet = oddNumbers.intersection(primeNumbers)  // [3, 5, 7]

// Subtraction
let differenceSet = oddNumbers.subtracting(primeNumbers)  // [1]

// Symmetric Difference
let symmetricDifferenceSet = oddNumbers.symmetricDifference(primeNumbers)  // [1, 2]
```
## Set Membership and Equality

Sets provide methods to check relationships between two sets.

### Set Relationships:

-   **isSubset(of:)**: Checks if all elements of one set are contained in another.
-   **isSuperset(of:)**: Checks if a set contains all elements of another set.
-   **isDisjoint(with:)**: Returns true if two sets have no elements in common.
```swift
let houseAnimals: Set = ["Cat", "Dog"]
let farmAnimals: Set = ["Cow", "Chicken", "Sheep", "Dog", "Cat"]
let cityAnimals: Set = ["Pigeon", "Rat"]

houseAnimals.isSubset(of: farmAnimals)    // true
farmAnimals.isSuperset(of: houseAnimals)  // true
houseAnimals.isDisjoint(with: cityAnimals)  // true
```
## Iterating Over a Set

Since sets are unordered, iterating over a set doesn’t guarantee element order.
```swift
for genre in favoriteGenres {
    print(genre)
}
// You can also sort the set when iterating
for genre in favoriteGenres.sorted() {
    print(genre)
}
```
## Set Properties and Methods

Here are a few commonly used properties and methods of sets:
```swift
.isEmpty      // Checks if the set is empty
.count        // Returns the number of elements in the set
.insert()     // Inserts a new element
.remove()     // Removes a specified element
.contains()   // Checks if the set contains a specified element
```
## Set vs NSSet

Similar to arrays, Swift has its own `Set` type, while Objective-C has `NSSet`. If you’re working with Objective-C APIs, you may need to bridge between them.