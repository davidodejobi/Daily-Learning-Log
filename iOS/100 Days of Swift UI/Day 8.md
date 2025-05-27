# Swift Functions: Default Parameter Values

## 🧠 Key Concepts

* Default values make parameters **optional**.
* Use when you want flexibility but with sensible defaults.
* Lets you simplify function calls.

## 🔤 Example: Times Tables with Default End Value

```swift
func printTimesTables(for number: Int, end: Int = 12) {
    for i in 1...end {
        print("\(i) x \(number) is \(i * number)")
    }
}

printTimesTables(for: 5, end: 20)
printTimesTables(for: 8)  // Uses default end = 12
```

* You can specify `end`, or leave it out and use 12 by default.

## 🏃‍♂️ Real-World Example: Array `removeAll()`

```swift
var characters = ["Lana", "Pam", "Ray", "Sterling"]
print(characters.count)
characters.removeAll()
print(characters.count)
characters.removeAll(keepingCapacity: true)
```

* `keepingCapacity` is a **Boolean defaulted to false**.
* `removeAll()` clears the array; optional `keepingCapacity: true` keeps array’s memory allocation.

## ✅ Syntax

* Place default value after the type in the parameter list.

```swift
func functionName(parameter: Type = defaultValue) {
    // function body
}
```

## 🔍 Summary

* **Default values** reduce code clutter and make calls simpler.
* Great for parameters where a common value is often used.
* Function calls can omit parameters with defaults.

---

