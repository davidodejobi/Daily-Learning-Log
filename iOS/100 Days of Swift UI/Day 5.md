# Swift `if` Statements and Conditional Logic

## ✅ What is an `if` Statement?

* Swift uses `if` statements to make decisions based on conditions.
* Syntax:

```swift
if condition {
    // code to run if condition is true
}
```

* The condition must evaluate to a **Boolean** (`true` or `false`).

## 🔍 Example: Exam Score Check

```swift
let score = 85
if score > 80 {
    print("Great job!")
}
```

* `>` is a **comparison operator**.
* Other comparison operators: `<`, `>=`, `<=`, `==`, `!=`

## 🔣 Braces and Code Blocks

* Use `{ }` to define code blocks.
* All code inside `{ }` runs only if the condition is `true`.
* **Always use braces**, even for one-liners, to improve readability and avoid bugs.

## 💡 Multiple Lines in Condition

```swift
if score > 80 {
    print("Well done!")
    print("You passed with distinction!")
}
```

## 🧪 Example: Real-World Checks

```swift
let speed = 88
let percentage = 85
let age = 18

if speed >= 88 {
    print("Where we're going we don't need roads.")
}

if percentage < 85 {
    print("Sorry, you failed the test.")
}

if age >= 18 {
    print("You're eligible to vote")
}
```

## 📚 Comparing Strings Alphabetically

```swift
let ourName = "Dave Lister"
let friendName = "Arnold Rimmer"

if ourName < friendName {
    print("It's \(ourName) vs \(friendName)")
} else {
    print("It's \(friendName) vs \(ourName)")
}
```

* String comparisons are based on **alphabetical (Unicode) order**.

## 🧰 Condition: Array Size Check

```swift
var numbers = [1, 2, 3]
numbers.append(4)

if numbers.count > 3 {
    numbers.remove(at: 0)
}

print(numbers)
```

## 🧑‍💻 Empty Input Handling

```swift
var username = ""

if username == "" {
    username = "Anonymous"
}

print("Welcome, \(username)!")
```

### Alternatives:

```swift
if username.count == 0 {
    username = "Anonymous"
}
```

```swift
if username.isEmpty {
    username = "Anonymous"
}
```

## ✅ Why `isEmpty` is Better

* `.count == 0` must traverse the whole string.
* `.isEmpty` is optimized: it stops as soon as content is found.
* Works with `String`, `Array`, `Set`, `Dictionary`, etc.

## 🧠 Important Notes

* Swift does **not** support truthy/falsy like some languages; conditions **must** be Boolean.
* Always ensure variables in conditions are fully initialized.
* Enforce code clarity with braces for all conditions.
* Condition logic can be combined or extended using `else`, `else if`, and `guard` (in future lessons).

## 📌 Summary

* `if` statements let you run code based on Boolean conditions.
* Use comparison operators: `==`, `!=`, `>`, `<`, `>=`, `<=`.
* Prefer `.isEmpty` to check for empty collections or strings.
* Swift requires Boolean values in all conditions.
* Always use `{}` braces for readability and safety.

---

# Swift `if`, `else`, and Advanced Condition Logic

## ✅ Basic `if` and `else` Structure

```swift
let age = 16

if age >= 18 {
    print("You can vote in the next election.")
} else {
    print("Sorry, you're too young to vote.")
}
```

* `if` runs when the condition is `true`.
* `else` runs when the condition is `false`.
* This avoids evaluating mutually exclusive conditions separately.

## 🧱 `else if` Chains

```swift
let a = false
let b = true

if a {
    print("Code to run if a is true")
} else if b {
    print("Code to run if a is false but b is true")
} else {
    print("Code to run if both a and b are false")
}
```

* Use `else if` for multiple branching conditions.
* Only **one** `else` is allowed (it must come last).

## 🔗 Combining Conditions with Logical Operators

### ✅ `&&` (Logical AND)

```swift
let temp = 25

if temp > 20 && temp < 30 {
    print("It's a nice day.")
}
```

* Condition only passes if **both** comparisons are `true`.

### ✅ `||` (Logical OR)

```swift
let userAge = 14
let hasParentalConsent = true

if userAge >= 18 || hasParentalConsent {
    print("You can buy the game")
}
```

* Condition passes if **either** side is `true`.

## 📦 Complex Conditions + Enums Example

```swift
enum TransportOption {
    case airplane, helicopter, bicycle, car, scooter
}

let transport = TransportOption.airplane

if transport == .airplane || transport == .helicopter {
    print("Let's fly!")
} else if transport == .bicycle {
    print("I hope there's a bike path…")
} else if transport == .car {
    print("Time to get stuck in traffic.")
} else {
    print("I'm going to hire a scooter now!")
}
```

### 🧠 Key Learnings from the Enum Example

* Use `||` to combine checks for multiple values.
* Enums provide a safe and structured way to represent states.
* After setting `transport` once, you can omit the enum type from future comparisons.

## ✅ Summary

* Use `if` for simple condition checks.
* Use `else` to handle the opposite case.
* Use `else if` to handle multiple conditions.
* Use `&&` for "and" logic; use `||` for "or" logic.
* Enums + logic = clean, scalable decision handling.

This layered condition structure helps you build flexible, readable logic in Swift apps.

---

# Swift `switch` Statements and Pattern Matching

## 🧠 Why Use `switch` Instead of `if`?

* Avoids repeated comparisons to the same value.
* Prevents mistakes like duplicate or missing cases.
* Enforces **exhaustiveness**: all possible values must be covered.
* Cleaner and easier to read when comparing a single value to multiple possibilities.

## 🔁 Basic Example Using Enum

```swift
enum Weather {
    case sun, rain, wind, snow, unknown
}

let forecast = Weather.sun

switch forecast {
case .sun:
    print("It should be a nice day.")
case .rain:
    print("Pack an umbrella.")
case .wind:
    print("Wear something warm")
case .snow:
    print("School is cancelled.")
case .unknown:
    print("Our forecast generator is broken!")
}
```

### ✅ Key Points

* `switch` starts with the value to compare: `switch forecast`.
* Each `case` compares a possible value using shorthand (`.value` instead of `Enum.value`).
* Swift checks each case **top to bottom**, runs the first match, then **stops**.

## 🚫 Common Mistakes

* Repeating cases (e.g. checking `.rain` twice).
* Forgetting to include all cases (Swift will refuse to compile).

## 🧪 Switching on Strings

```swift
let place = "Metropolis"

switch place {
case "Gotham":
    print("You're Batman!")
case "Mega-City One":
    print("You're Judge Dredd!")
case "Wakanda":
    print("You're Black Panther!")
default:
    print("Who are you?")
}
```

* Use `default` for unmatched values.
* `default` must come **last**.

## 🧰 Using `fallthrough`

* Swift does **not** automatically continue to the next case.
* Use `fallthrough` explicitly to continue executing the next case.

### Without `fallthrough`

```swift
let day = 5
print("My true love gave to me…")

switch day {
case 5:
    print("5 golden rings")
case 4:
    print("4 calling birds")
case 3:
    print("3 French hens")
case 2:
    print("2 turtle doves")
default:
    print("A partridge in a pear tree")
}
```

### With `fallthrough`

```swift
let day = 5
print("My true love gave to me…")

switch day {
case 5:
    print("5 golden rings")
    fallthrough
case 4:
    print("4 calling birds")
    fallthrough
case 3:
    print("3 French hens")
    fallthrough
case 2:
    print("2 turtle doves")
    fallthrough
default:
    print("A partridge in a pear tree")
}
```

* This example builds up from the highest matched case to the default.
* `fallthrough` continues to execute all the remaining code blocks.

## 📌 Summary

* Use `switch` when comparing a single value against multiple possibilities.
* Swift enforces **exhaustiveness** for enums.
* Use `default` when you can't list all possible values.
* Use `fallthrough` **sparingly** – only when necessary.
* Improves code clarity, safety, and correctness over chained `if-else if` statements.
