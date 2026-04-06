# Classes & Structures

Classes and structures are used to create custom data types in Swift. They allow you to group related properties (data) and methods (functions) together.

At a glance, they look very similar — but they behave very differently under the hood.


## Defining a Structure

A `struct` is a value type.

```swift
struct Person {
    var name: String
    var age: Int
}
```

#### Creating an Instance

```swift
var person1 = Person(name: "John", age: 25)
print(person1.name)  // John
```

## Defining a Class

A `class` is a reference type.

```swift
class Person {
    var name: String
    var age: Int
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
}
```

#### Creating an Instance

```swift
let person1 = Person(name: "John", age: 25)
print(person1.name)  // John
```

## Key Difference: Value Type vs Reference Type

This is the most important difference.

#### Structures (Value Type)

When you assign or pass a struct, it gets **copied**.

```swift
var person1 = Person(name: "John", age: 25)
var person2 = person1

person2.name = "Mike"

print(person1.name)  // John
print(person2.name)  // Mike
```

#### Classes (Reference Type)

When you assign or pass a class, it shares the **same reference**.

```swift
let person1 = Person(name: "John", age: 25)
let person2 = person1

person2.name = "Mike"

print(person1.name)  // Mike
print(person2.name)  // Mike
```

## Mutability

### Structures

If a struct instance is declared with `let`, it becomes immutable.

```swift
let person = Person(name: "John", age: 25)
// person.age = 30  ❌ Error
```
### Classes

Even if a class instance is declared with `let`, its properties can still change.
```swift
let person = Person(name: "John", age: 25)
person.age = 30  // ✅ Allowed
```

## Methods

Both classes and structures can have methods.

```swift
struct Rectangle {
    var width: Double
    var height: Double
    
    func area() -> Double {
        return width * height
    }
}

let rect = Rectangle(width: 10, height: 5)
print(rect.area())  // 50
```

## Mutating Methods (Structs Only)

To modify properties inside a struct method, use `mutating`.

```swift
struct Counter {
    var value = 0
    
    mutating func increment() {
        value += 1
    }
}

var counter = Counter()
counter.increment()
```
## Initializers

### Struct Initializer (Auto-generated)

Structs automatically get a memberwise initializer.

```swift
let person = Person(name: "John", age: 25)
```

### Class Initializer (Manual)

Classes require you to define an initializer.

```swift
init(name: String, age: Int) {
    self.name = name
    self.age = age
}
```
## Inheritance (Classes Only)

Classes can inherit from other classes, structs cannot.

```swift
class Animal {
    func speak() {
        print("Some sound")
    }
}

class Dog: Animal {
    override func speak() {
        print("Bark")
    }
}
```
## Type Casting

Used mostly with classes when working with inheritance.

```swift
let animal: Animal = Dog()

if let dog = animal as? Dog {
    dog.speak()
}
```

## Deinitializers (Classes Only)

Classes can clean up resources when an instance is removed from memory.

```swift
class FileHandler {
    deinit {
        print("File closed")
    }
}
```
## Struct vs Class Summary

|Feature|Struct|Class |
|-----|-----|-----|
|Type|Value Type|Reference Type |
|Copy Behavior|Copied|Shared Reference |
|Mutability|Immutable with `let`|Mutable even with `let` |
|Initializer|Auto|Manual|
|Inheritance|❌ No|✅ Yes |
|Deinitializer|❌ No|✅ Yes |

## When to Use Struct vs Class

### Use Struct when:

-   You want **value semantics (copying)**
-   Data is simple and lightweight
-   You don’t need inheritance
-   You want safer, predictable behavior

### Use Class when:

-   You need **shared state**
-   You require inheritance
-   You’re working with reference-based logic (like UIKit)

----------

## Common Real-world Examples

-   **Structs** → Models, data containers, API responses
-   **Classes** → ViewControllers, Managers, Services

> **Note**: In Swift, prefer **structs by default**.
Switch to classes only when you specifically need : 1) shared references , 2)  inheritance.
This is actually a common interview question too.