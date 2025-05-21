# Swift Type Annotations

## 🧠 What Are Type Annotations?

* **Type inference**: Swift figures out the type based on the value you assign.
* **Type annotation**: You explicitly state what type a variable or constant should be.

## ✍️ Basic Syntax

```swift
let surname: String = "Lasso"
var score: Int = 0
```

Equivalent using type inference:

```swift
let surname = "Lasso"
var score = 0
```

## 🎯 Why Use Type Annotations?

* To **override** Swift’s type inference.
* To **declare** variables/constants without giving them a value yet.

```swift
var score: Double = 0  // Overrides default Int
```

## 📚 Common Swift Types

| Type          | Description              | Example                                             |
| ------------- | ------------------------ | --------------------------------------------------- |
| `String`      | Text                     | `let player: String = "Roy"`                        |
| `Int`         | Whole numbers            | `var luckyNumber: Int = 13`                         |
| `Double`      | Decimal numbers          | `let pi: Double = 3.141`                            |
| `Bool`        | `true` or `false` values | `var isAuthenticated: Bool = true`                  |
| `[Type]`      | Array of a specific type | `var albums: [String] = ["Red"]`                    |
| `[Key:Value]` | Dictionary               | `var user: [String: String] = ["id": "@twostraws"]` |
| `Set<Type>`   | Set of unique values     | `var books: Set<String> = Set(["Book A"])`          |

## 📥 Declaring Empty Collections

```swift
var teams: [String] = [String]()
var cities: [String] = []
var clues = [String]() // Type inferred
```

## 🆕 Enums with Type Annotations

```swift
enum UIStyle {
    case light, dark, system
}

var style: UIStyle = .light
style = .dark
```

## ⚠️ Constants Without Initial Values

You can declare a constant without a value, but **must** use a type annotation:

```swift
let username: String
// ... more logic
username = "@twostraws"
```

* Value must be assigned **before first use**.
* Value can only be set **once**.

## ❌ Invalid Type Assignments

```swift
let score: Int = "Zero"  // ❌ Error: cannot assign String to Int
```

## ✅ Summary

* Swift uses type inference by default.
* Use type annotations when:

  * You want a **different type** than Swift infers.
  * You declare a constant/variable **without a value**.
* Swift must always know what type your variables and constants hold — this is part of being a **type-safe language**.

Knowing when and how to use type annotations helps you write safer, clearer, and more flexible Swift code.

---

# Swift Collections Recap

## 📦 Arrays

* Store multiple values of the same type in a **specific order**.
* Access values using **integer indices** (zero-based).
* Must be specialized: `[String]`, `[Int]`, etc.
* Common methods:

  * `.count` – total number of items
  * `.append(value)` – add a new item
  * `.contains(value)` – check for an item

```swift
var fruits = ["Apple", "Banana"]
fruits.append("Orange")
print(fruits[0]) // Apple
```

## 📘 Dictionaries

* Store key-value pairs.
* Access values using **keys**, not index.
* Must be specialized: `[KeyType: ValueType]`, e.g., `[String: String]`
* Common methods:

  * `.count`
  * `.contains(where:)`
  * Access with default: `dict[key, default: value]`

```swift
var user = ["name": "Alice", "role": "Admin"]
print(user["name", default: "Unknown"])
```

## 🔹 Sets

* Store unique values with **no specific order**.
* Must be specialized: `Set<Type>`
* Super fast `.contains()` check.
* Removes duplicates automatically.

```swift
var ids = Set([1, 2, 3])
ids.insert(4)
print(ids.contains(2)) // true
```

## 🎛 Enums

* Define a **fixed set of related values**.
* Useful for creating **custom data types**.
* Syntax:

```swift
enum Direction {
    case north, south, east, west
}

var heading = Direction.north
heading = .west
```

## 🔍 Type Safety

* Swift always needs to know the **type** of your constants or variables.
* Uses **type inference** based on the assigned value.
* Use **type annotations** to be explicit or when no value is assigned yet.

```swift
let city: String = "Lagos"
var scores = [Int]()
```

## ✅ Summary

* **Arrays**: Most common – store ordered data with duplicates.
* **Dictionaries**: Keyed data access, great for named records.
* **Sets**: Fast, unique storage – ideal for membership checks.
* **Enums**: Build your own data types with controlled values.
* **Type annotations**: Help Swift understand what kind of data you’re working with, especially when values aren't assigned immediately.

Arrays are your go-to tool, with dictionaries next in usefulness. Sets have their place too – especially for performance-sensitive membership checks.
