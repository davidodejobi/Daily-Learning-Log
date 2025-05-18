# Running the Book’s Code

## Key Concepts
- All sample code in the book should be **typed and tested by you**.
- You'll use **Xcode Playgrounds** to run Swift code easily.
- Playgrounds show results live next to your code – perfect for learning.

## Xcode Playground Setup (macOS)
1. **Install Xcode 15+**
   - Get it from the **Mac App Store** (free).

2. **Create a Playground**
   - Open Xcode → `File ▸ New ▸ Playground…`
   - Select `Blank` under the **macOS** tab.
   - Save it somewhere easy to find (e.g. `Documents/SwiftBook.playground`)

3. **Try It Out**
```swift
var greeting = "Hello, Swift!"
print(greeting) // ⇒ Hello, Swift!
```
- The first run may take a few seconds; later ones are faster.

4. **Tips**
- Use one playground for the entire book, or a new one per chapter.
- Code changes are reflected live—experiment freely!

## Alternatives if You Don’t Have a Mac

### 1. Swift Playgrounds (iPad)
- Free from the iPad App Store.
- Create a blank playground and follow along with the same Swift syntax.

### 2. Online Swift REPLs
- Use in any browser:
  - [SwiftFiddle](https://swiftfiddle.com)
  - [Replit](https://replit.com)
- Great for small tests and quick practice.

## Checklist
- [ ] Code runs and prints the correct output.
- [ ] You've edited and tested code variations.
- [ ] You have a playground or online setup ready to continue learning.

🧠 **Best Practice:** Reading is not enough—**run the code, break it, and learn by doing**!


---


# Variables and Constants in Swift

## Key Concepts
- **Variables** are used to store values that can change over time.
- **Constants** are used to store values that never change.
- Swift encourages the use of **constants (`let`)** whenever possible for safety and performance.
- Use **`print()`** to view variable values in a playground during development.
- Swift uses **camelCase** for naming variables and constants.

## Variables (`var`)
- Use `var` to declare a variable (i.e., a value that can change).

```swift
var greeting = "Hello, playground"
greeting = "Hi there"
```

- You can reassign a variable without using `var` again:

```swift
var name = "Ted"
name = "Rebecca"
name = "Keeley"
```

- Old values are **discarded** as soon as a new one is assigned.

## Constants (`let`)
- Use `let` to declare a constant (i.e., a value that can’t change).

```swift
let character = "Daphne"
```

- Trying to change a constant will cause a **compiler error**:

```swift
let character = "Daphne"
//character = "Eloise"   // ❌ Error: Cannot assign to value: 'character' is a 'let' constant
//character = "Francesca" // ❌ Error: Same here
```

- Always prefer `let` over `var` when you don’t need to change the value.

## 🖨 Printing Values
- Use `print()` to inspect the current value of a variable:

```swift
var playerName = "Roy"
print(playerName)

playerName = "Dani"
print(playerName)

playerName = "Sam"
print(playerName)
```

- This is helpful in **Playgrounds** but not typically used in production apps.

## Syntax Breakdown
1. `var` or `let` — keyword to declare variable or constant.
2. `name` — your identifier, can be anything but should be descriptive.
3. `=` — assignment operator.
4. `"value"` — the assigned value, enclosed in double quotes for strings.

## Tips
- Swift does **not require semicolons** at the end of lines.
- Use **camelCase** for naming: `playerName`, `dogBreed`, `meaningOfLife`.
- Always use the same name consistently; `playerName` and `playername` are different in Swift.
- The `import Cocoa` statement in macOS Playgrounds gives access to Apple’s UI frameworks (important—don’t delete it).

## Best Practice
- Prefer `let` over `var` unless you **know** you need to change the value later. This leads to:
  - Safer code (fewer unintended changes)
  - Better performance (compiler optimization)

---

# Swift Strings Basics

## Key Concepts

* A **string** is a series of characters (letters, punctuation, emoji, etc.).
* Strings are created using **double quotes**: `"Hello"`.
* Strings can include escaped double quotes using a **backslash**: `\"`.
* Swift strings support **multi-line strings** using triple quotes: `"""`.
* Strings are **case-sensitive**.

## Basic String Syntax

```swift
let actor = "Denzel Washington"
let filename = "paris.jpg"
let result = "⭐️ You win! ⭐️"
let quote = "Then he tapped a sign saying \"Believe\" and walked away."
```

## Multi-line Strings
Use triple quotes for multi-line string literals:

```swift
let movie = """
A day in
the life of an
Apple engineer
"""
```

## Useful String Properties and Methods

### 1. Get String Length

```swift
print(actor.count) // 17
let nameLength = actor.count
print(nameLength)  // 17
```

* `.count` is a **property**, so no parentheses are needed.

### 2. Convert to Uppercase

```swift
print(result.uppercased())
```

* `.uppercased()` is a **method** that returns an uppercase version of the string.
* Note: Some methods in Swift do not require parentheses when called without arguments, but `uppercased()` always requires them.

### 3. Check Prefix

```swift
print(movie.hasPrefix("A day"))
```

### 4. Check Suffix

```swift
print(filename.hasSuffix(".jpg")) // true
print(filename.hasSuffix(".JPG")) // false (case-sensitive)
```

## Notes

* Use `.count` for getting length.
* Use `.uppercased()` to convert string to uppercase.
* Use `.hasPrefix()` and `.hasSuffix()` to check string beginnings and endings.
* Remember: Strings are case-sensitive.

## Summary
Swift strings are versatile and powerful. Start by mastering these basics:

* Creating and printing strings
* Using properties like `.count`
* Using methods like `.uppercased()`, `.hasPrefix()`, and `.hasSuffix()`

This foundation will help you work confidently with text in Swift.


---

# Swift Strings Basics

## 🧠 Key Concepts

* A **string** is a series of characters (letters, punctuation, emoji, etc.).
* Strings are created using **double quotes**: `"Hello"`.
* Strings can include escaped double quotes using a **backslash**: `\"`.
* Swift strings support **multi-line strings** using triple quotes: `"""`.
* Strings are **case-sensitive**.

## 🄤 Basic String Syntax

```swift
let actor = "Denzel Washington"
let filename = "paris.jpg"
let result = "⭐️ You win! ⭐️"
let quote = "Then he tapped a sign saying \"Believe\" and walked away."
```

## 📏 Multi-line Strings
Use triple quotes for multi-line string literals:

```swift
let movie = """
A day in
the life of an
Apple engineer
"""
```

## 🔧 Useful String Properties and Methods

### 1. Get String Length

```swift
print(actor.count) // 17
let nameLength = actor.count
print(nameLength)  // 17
```

* `.count` is a **property**, so no parentheses are needed.

### 2. Convert to Uppercase

```swift
print(result.uppercased())
```

* `.uppercased()` is a **method** that returns an uppercase version of the string.
* Note: Some methods in Swift do not require parentheses when called without arguments, but `uppercased()` always requires them.

### 3. Check Prefix

```swift
print(movie.hasPrefix("A day"))
```

### 4. Check Suffix

```swift
print(filename.hasSuffix(".jpg")) // true
print(filename.hasSuffix(".JPG")) // false (case-sensitive)
```

## Notes

* Use `.count` for getting length.
* Use `.uppercased()` to convert string to uppercase.
* Use `.hasPrefix()` and `.hasSuffix()` to check string beginnings and endings.
* Some methods like `isEmpty` can be used without parentheses: `string.isEmpty`.
* Remember: Strings are case-sensitive.

## Summary
Swift strings are versatile and powerful. Start by mastering these basics:

* Creating and printing strings
* Using properties like `.count`
* Using methods like `.uppercased()`, `.hasPrefix()`, and `.hasSuffix()`

This foundation will help you work confidently with text in Swift.


---

# Swift Integers Basics

## Key Concepts

* Whole numbers like 3, 5, 50, or 5\_000\_000 are called **integers** in Swift.
* Swift uses the `Int` type to represent integers.
* You can use `let` or `var` to declare integers, just like strings.

```swift
let score = 10
```

* Integers can be **positive** or **negative**, and can go up to quintillions.

## Readable Numbers
You can add underscores (`_`) to make large numbers easier to read:

```swift
let reallyBig = 100_000_000
let weirdStyle = 1_00__00___00____00 // Still valid!
```

## Basic Arithmetic Operations
You can perform arithmetic with integers using these operators:

```swift
let lowerScore = score - 2
let higherScore = score + 10
let doubledScore = score * 2
let squaredScore = score * score
let halvedScore = score / 2
```

## Compound Assignment Operators
Instead of reassigning manually, use shorthand:

```swift
var counter = 10
counter += 5   // Add 5
counter *= 2   // Multiply by 2
counter -= 10  // Subtract 10
counter /= 2   // Divide by 2
```

## Useful Integer Methods
Use `.isMultiple(of:)` to check for multiples:

```swift
let number = 120
print(number.isMultiple(of: 3))
print(120.isMultiple(of: 3)) // Also works directly
```

## Summary

* Integers are declared with `let` or `var`, and use the `Int` type.
* Underscores help format large numbers: `1_000_000`
* Use `+`, `-`, `*`, `/` for arithmetic.
* Use `+=`, `-=`, `*=`, `/=` for compound updates.
* Check if a number is a multiple with `.isMultiple(of:)`.

---


# Swift Floating-Point Numbers Basics

## Key Concepts

* Numbers with a decimal point like `3.1`, `5.56`, or `3.141592654` are called **floating-point numbers** in Swift.
* Swift uses the `Double` type by default for decimal numbers ("double-precision floating-point").
* These numbers are stored in a format that allows for very large or very small values by **"floating" the decimal point**.
* Floating-point math is **not always exact** because binary cannot precisely represent some decimals.

```swift
let number = 0.1 + 0.2
print(number) // Output: 0.30000000000000004
```

## Type Safety Between Int and Double

* Swift treats `Int` and `Double` as **different types**.
* You can't directly mix them in operations:

```swift
let a = 1
let b = 2.0
let c = a + b // Error: Cannot add Int and Double
```

To fix it, convert one to match the other:

```swift
let c = a + Int(b)       // Convert Double to Int
let c2 = Double(a) + b   // Convert Int to Double
```

## Swift's Type Inference

* If a number has a dot (`.`), Swift assumes it’s a `Double`:

```swift
let double1 = 3.1
let double2 = 3131.3131
let double3 = 3.0 // Still Double
let int1 = 3      // Int
```

## Reassigning Variables and Type Consistency

* Once Swift infers a type, you must keep using that type:

```swift
var name = "Nicolas Cage"
name = "John Travolta" // OK
name = 57              // Error: type mismatch
```

## ➕ Arithmetic with Doubles

* You can use all arithmetic and compound operators just like with `Int`:

```swift
var rating = 5.0
rating *= 2  // rating is now 10.0
```

## CGFloat

* Some older APIs (especially in UIKit) use `CGFloat` for decimal values.
* Swift lets you use `Double` anywhere `CGFloat` is expected, so conversions are automatic in most cases.

## Why Floating-Point is Inexact

* Computers store numbers in **binary**, so some decimals can’t be perfectly represented.
* Example: `1 / 3` equals `0.333…`, which is repeating and cannot be stored precisely.
* These small inaccuracies are usually harmless but explain why Swift enforces **strict type safety**.

## Summary

* Decimal numbers use the `Double` type in Swift.
* You can't mix `Int` and `Double` without explicit conversion.
* Use arithmetic operators like `+`, `-`, `*`, `/` just like with integers.
* Floating-point precision errors are normal in computing and stem from binary representation limitations.

