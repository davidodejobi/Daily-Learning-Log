# Swift Booleans Basics

## 🧠 Key Concepts

* A **Boolean** is a simple data type that stores either `true` or `false`.
* Named after mathematician **George Boole**, Booleans are often used to represent binary logic or decision-making conditions.
* Booleans are returned from expressions like `.hasSuffix()` or `.isMultiple(of:)`.

```swift
let filename = "paris.jpg"
print(filename.hasSuffix(".jpg")) // true

let number = 120
print(number.isMultiple(of: 3)) // true
```

## ✅ Creating Booleans

```swift
let goodDogs = true
let gameOver = false
```

Booleans can also be assigned from expressions:

```swift
let isMultiple = 120.isMultiple(of: 3)
```

## ❌ Boolean Operators

* Booleans don’t support arithmetic (`+`, `-`, etc.).
* But they **do** support the **logical NOT operator (`!`)**:

```swift
var isAuthenticated = false
isAuthenticated = !isAuthenticated // now true
print(isAuthenticated)

isAuthenticated = !isAuthenticated // now false
print(isAuthenticated)
```

## 🔄 Boolean Toggle

* Use `.toggle()` to flip a Boolean’s value:

```swift
var gameOver = false
print(gameOver) // false

gameOver.toggle()
print(gameOver) // true
```

* This does the same thing as `gameOver = !gameOver` but is often more readable in logic-heavy code.

## 🧾 Summary

* Booleans hold either `true` or `false`.
* Commonly used in conditions and logic checks.
* Use `!` to flip values and `.toggle()` to simplify flipping.
* Returned from methods like `.hasPrefix()`, `.isMultiple(of:)`, etc.

---

# Swift String Concatenation and Interpolation

## 🔗 Concatenation with `+`

* You can join strings using the `+` operator:

```swift
let firstPart = "Hello, "
let secondPart = "world!"
let greeting = firstPart + secondPart
```

* You can concatenate multiple strings:

```swift
let people = "Haters"
let action = "hate"
let lyric = people + " gonna " + action
print(lyric) // Haters gonna hate
```

* The `+=` operator appends to an existing string:

```swift
var slogan = "Just "
slogan += "do it."
```

## ⚠️ Performance Consideration

* Using `+` repeatedly creates temporary strings, which can be inefficient:

```swift
let code = "1" + "2" + "3" + "4" + "5" // inefficient
```

Each `+` creates a new intermediate result, wasting memory.

## 💡 String Interpolation

* Preferred way to insert values into strings.
* Use `\()` inside string literals:

```swift
let name = "Taylor"
let age = 26
let message = "Hello, my name is \(name) and I'm \(age) years old."
print(message)
```

* Interpolation can include any type (Int, Double, etc.):

```swift
let number = 11
let mission = "Apollo \(number) landed on the moon."
```

* You can perform calculations directly:

```swift
let base = 5
let height = 10
let area = "Triangle area is \(0.5 * Double(base) * Double(height))"
```

## 🚫 Mixing Types with `+`

* Swift does **not** allow mixing types like `String + Int` directly:

```swift
let number = 11
let msg = "Apollo " + number + " landed." // ❌ Error
```

* You must convert manually:

```swift
let msg = "Apollo " + String(number) + " landed."
```

* Interpolation handles it automatically and cleanly:

```swift
let msg = "Apollo \(number) landed."
```

## ✅ Summary

* Use `+` or `+=` for basic string joining.
* Prefer **string interpolation** for inserting values.
* It's more efficient, readable, and allows expressions and type conversion inside strings.


---


# Swift Data Basics Recap

## 🧱 Constants and Variables

* Use `let` to declare constants (values that don’t change).
* Use `var` to declare variables (values that can change).
* Prefer `let` when possible to help avoid bugs.

## 📝 Strings

* Represent text and support any characters, including emoji and international scripts.
* Created using double quotes:

  ```swift
  let greeting = "Hello"
  ```
* Multi-line strings use triple quotes:

  ```swift
  let message = """
  Line 1
  Line 2
  """
  ```
* Common properties and methods:

  * `.count` – returns the number of characters.
  * `.uppercased()` – returns the string in all uppercase letters.

## 🔢 Integers (Int)

* Whole numbers, both positive and negative.
* Example:

  ```swift
  let score = 100
  print(score.isMultiple(of: 5))
  ```

## 🔣 Doubles (Decimal Numbers)

* `Double` represents decimal values.
* Can hold very large or small numbers, but not 100% accurate.
* Not suitable for exact precision needs (e.g., money).
* Example:

  ```swift
  let pi = 3.14159
  ```

## ➕ Arithmetic

* Operators: `+`, `-`, `*`, `/`
* Compound assignment: `+=`, `-=`, `*=`, `/=`

## ✅ Booleans

* Store `true` or `false` values.
* Can be flipped using `!` or `.toggle()`:

  ```swift
  var isOn = false
  isOn.toggle()
  ```

## 💬 String Interpolation

* Insert variables and constants directly into strings:

  ```swift
  let name = "Alex"
  let age = 30
  let message = "My name is \(name) and I am \(age) years old."
  ```
* More efficient and flexible than using `+`.

## 🧾 Summary

* You’ve learned how to use:

  * `let` and `var`
  * Strings and multi-line text
  * Integers and doubles
  * Arithmetic and compound operators
  * Booleans and toggling
  * String interpolation

These are foundational tools in Swift development. You’ll keep using them until they become second nature.
