# Protocols

A `protocol` defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality.

Think of it as:
> “Any type that follows this protocol must implement these rules.”

Protocols themselves don’t provide implementation — they only define what needs to be implemented.

## Defining a Protocol

```swift
protocol Vehicle {
    var speed: Int { get set }
    
    func accelerate()
}
```

## Conforming to a Protocol

A class, struct, or enum can conform to a protocol by implementing its requirements.

```swift
struct Car: Vehicle {
    var speed: Int = 0
    
    func accelerate() {
        print("Car is accelerating")
    }
}
```

## Using Protocols

```swift
let myCar = Car()
myCar.accelerate()
```

## Property Requirements

Protocols can require properties with `{ get }` or `{ get set }`.

```swift
protocol Person {
    var name: String { get }
    var age: Int { get set }
}
```
>  Note: 
> `{ get }` → Read-only 
> `{ get set }` → Read & Write

## Method Requirements

Protocols can define instance methods or type methods.

```swift
protocol Animal {
    func makeSound()
}
```

## Mutating Methods (Structs / Enums)

If a protocol method modifies the instance, mark it as `mutating`.

```swift
protocol Toggleable {
    mutating func toggle()
}

struct Switch: Toggleable {
    var isOn = false
    
    mutating func toggle() {
        isOn.toggle()
    }
}
```

## Protocols with Classes (AnyObject)

You can restrict a protocol to class types only.

```swift
protocol NetworkDelegate: AnyObject {
    func didReceiveData()
}
```

## Protocol Inheritance

Protocols can inherit from other protocols.

```swift
protocol LivingBeing {
    func breathe()
}

protocol Human: LivingBeing {
    func speak()
}
```

## Protocol Composition

You can require multiple protocols at once.

```swift
protocol Flyable {
    func fly()
}

protocol Swimmable {
    func swim()
}

func performAction(entity: Flyable & Swimmable) {
    entity.fly()
    entity.swim()
}
```

## Protocol Extensions

Protocols can provide default implementations using extensions.

```swift
protocol Greetable {
    func greet()
}

extension Greetable {
    func greet() {
        print("Hello!")
    }
}
```
>  Now conforming types get a default implementation.
```swift
struct Person: Greetable {}

let person = Person()
person.greet()  // Hello!
```

## Optional Protocol Methods (Objective-C only)

Optional methods are only available for protocols marked with `@objc`.

```swift
@objc protocol OptionalProtocol {
    @objc optional func optionalMethod()
}
```
> Rarely used in pure Swift — more common when working with UIKit.

## Protocol as a Type

Protocols can be used as types.

```swift
func startVehicle(vehicle: Vehicle) {
    vehicle.accelerate()
}
```

## Delegation Pattern (Common Use Case)

Protocols are heavily used in delegation.

```swift
protocol DownloadDelegate {
    func didFinishDownload()
}

class Downloader {
    var delegate: DownloadDelegate?
    
    func finish() {
        delegate?.didFinishDownload()
    }
}
```
## Protocols vs Classes

-   **Protocols** → Define behavior (what to do)
-   **Classes/Structs** → Implement behavior (how to do it)


## When to Use Protocols

Use protocols when:

-   You want to define **shared behavior**
-   You need **loose coupling between components**
-   You’re implementing **delegation**
-   You want **flexibility and reusability**

## Common Real-world Examples

-   Delegates (UITableViewDelegate, etc.)
-   Networking layers
-   ViewModels (MVVM)
-   Dependency injection