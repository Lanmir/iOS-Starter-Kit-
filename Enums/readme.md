
# Enums

## What is an Enum?

An `enum` (short for *enumeration*) defines a group of related values in a type-safe way. Instead of using random strings or integers, enums let you represent a fixed set of possible states.

Think of enums as a way to say:  
> “This value can only be one of these specific options.”

```swift
enum Direction {
    case north
    case south
    case east
    case west
}
```
Now `Direction` can only ever be one of those four values — nothing else.

## Using Enums

You can create a variable of an enum type and assign one of its cases.

```swift
var currentDirection = Direction.north

// Swift can infer the type if already known
currentDirection = .east
```

## Enums with Switch

Enums are most commonly used with `switch` statements, because Swift forces you to handle all possible cases.

```swift
let direction: Direction = .south

switch direction {
case .north:
    print("Going up")
case .south:
    print("Going down")
case .east:
    print("Going right")
case .west:
    print("Going left")
}
```
>**Note:** Switch statements with enums must be exhaustive (handle all cases), or include a `default`.

## Raw Values

Enums can have **raw values**, which means each case is backed by a default value (like `Int` or `String`).

```swift
enum Planet: Int {
    case mercury = 1
    case venus
    case earth
    case mars
}
```
If you don’t assign values manually, Swift auto-increments them.

```swift
let earthOrder = Planet.earth.rawValue  // 3
```
You can also initialize enums using raw values:
```swift
let possiblePlanet = Planet(rawValue: 2)  // Optional(venus)
```

## String Raw Values

Very useful when working with APIs or readable data.

```swift
enum APIEndpoint: String {
    case users = "users_endpoint"
    case posts = "posts_endpoint"
}

print(APIEndpoint.users.rawValue)  // "users_endpoint"
```
## Associated Values

Enums can store **associated values**, meaning each case can carry additional data.

```swift
enum Result {
    case success(String)
    case failure(Int)
}
```

Usage:

```swift
let response = Result.success("Data received")

switch response {
case .success(let message):
    print(message)
case .failure(let code):
    print("Error code: \(code)")
}
```
>Note: This is extremely useful for handling API responses or states.

## Enums with Multiple Associated Values

```swift
enum LoginState {
    case loggedIn(username: String, token: String)
    case loggedOut
}
```

## Methods inside Enums

Enums can have methods just like classes or structs.

```swift
enum Direction {
    case north, south, east, west
    
    func description() -> String {
        switch self {
        case .north: return "Up"
        case .south: return "Down"
        case .east: return "Right"
        case .west: return "Left"
        }
    }
}

let dir = Direction.west
print(dir.description())  // Left
```
## Mutating Methods

If you want to change the enum value inside a method, use `mutating`.

```swift
enum SwitchState {
    case on, off
    
    mutating func toggle() {
        self = (self == .on) ? .off : .on
    }
}

var light = SwitchState.off
light.toggle()  // now .on
```
## CaseIterable

If you want to get all cases of an enum, conform to `CaseIterable`.

```swift
enum Beverage: CaseIterable {
    case coffee, tea, juice
}

for drink in Beverage.allCases {
    print(drink)
}
```
## Enums vs Raw Values vs Associated Values

-   **Raw Values** → fixed predefined values (like Int/String)
-   **Associated Values** → dynamic values attached at runtime
```swift
// Raw value
enum Status: Int {
    case success = 200
}

// Associated value
enum Response {
    case success(String)
}
```
## When to Use Enums

Use enums when:

-   You have a **fixed set of states**
-   You want **type safety** instead of strings/ints
-   You’re handling **different cases of data (especially APIs)**
-   You want **clean switch-based logic**

## Common Real-world Examples

-   Network states → loading, success, failure
-   UI states → idle, loading, error
-   Directions, categories, types
-   API responses / endpoints