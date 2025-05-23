# Swift `for` Loops – Practical Overview

## 🔁 Why Loops Matter

* Computers excel at repetitive tasks.
* Swift’s `for` loop lets you repeat code:

  * A fixed number of times.
  * For every item in an array, dictionary, or set.

---

## 📦 Looping Over Collections

```swift
let platforms = ["iOS", "macOS", "tvOS", "watchOS"]

for os in platforms {
    print("Swift works great on \(os).")
}
```

* `os` is the **loop variable**.
* The loop body runs once for each item in the array.
* `os` is only available inside the loop.

### 🧠 Terms to Know

* **Loop body** – the code inside `{}`.
* **Loop iteration** – one run of the loop body.
* **Loop variable** – `os`, `name`, or whatever you call it; scoped to the loop.

### Loop Variable Naming

```swift
for name in platforms {
    print("Swift works great on \(name).")
}

for rubberChicken in platforms {
    print("Swift works great on \(rubberChicken).")
}
```

* The variable name is up to you.
* Xcode suggests intelligent loop variable names using singular/plural inference.

---

## 🔢 Looping Over Ranges

```swift
for i in 1...12 {
    print("5 x \(i) is \(5 * i)")
}
```

* `1...12` creates a **closed range**.
* Common loop variable: `i`, `j`, `k`, etc.
* Each iteration gives a new value from 1 to 12.

---

## 🔁 Nested Loops

```swift
for i in 1...12 {
    print("The \(i) times table:")

    for j in 1...12 {
        print("  \(j) x \(i) is \(j * i)")
    }

    print() // Adds a blank line
}
```

* Useful for multi-dimensional data or multiplication tables.
* `print()` with no argument creates a blank line.

---

## 🔄 Half-Open Ranges: `..<`

```swift
for i in 1...5 {
    print("Counting from 1 through 5: \(i)")
}

print()

for i in 1..<5 {
    print("Counting 1 up to 5: \(i)")
}
```

* `...` includes the upper bound.
* `..<` excludes the upper bound.
* Read as: "1 through 5" vs. "1 up to 5".
* Useful for array indexing.

---

## 🔁 Looping Without a Variable

```swift
var lyric = "Haters gonna"

for _ in 1...5 {
    lyric += " hate"
}

print(lyric)
```

* Use `_` when you don’t need the loop variable.
* Keeps your code cleaner.

---

## ✅ Summary

* `for` loops repeat tasks over a sequence.
* Loop over arrays, dictionaries, sets, or ranges.
* Use `...` to include the upper bound, `..<` to exclude it.
* Replace unused loop variables with `_`.
* Combine loops for more complex operations.

---

# Swift `while` Loops

## 🔁 What Is a `while` Loop?

* Executes code **as long as a condition is true**.
* Less common than `for` loops but useful when the number of iterations isn't known beforehand.

---

## 🧮 Basic `while` Loop Example

```swift
var countdown = 10

while countdown > 0 {
    print("\(countdown)…")
    countdown -= 1
}

print("Blast off!")
```

* Starts from 10 and decrements down to 0.
* The loop stops when the condition `countdown > 0` becomes false.

---

## 🎲 Using `random(in:)` with `while`

### Generate Random Numbers

```swift
let id = Int.random(in: 1...1000)
let amount = Double.random(in: 0...1)
```

### Critical Hit Dice Rolling Example

```swift
var roll = 0

while roll != 20 {
    roll = Int.random(in: 1...20)
    print("I rolled a \(roll)")
}

print("Critical hit!")
```

* This continues until a 20 is rolled.
* `random(in:)` is useful for generating random values.

---

## 🆚 `for` vs `while`

| Feature     | `for` Loop                  | `while` Loop                      |
| ----------- | --------------------------- | --------------------------------- |
| Usage       | Known number of iterations  | Unknown number of iterations      |
| Best For    | Arrays, ranges, collections | Loops with custom exit conditions |
| Readability | Clear for fixed loops       | More flexible, less structured    |

---

## ✅ Summary

* Use `while` when the loop length depends on a condition, not a count.
* Loop continues **until the condition becomes false**.
* Great for working with randomness, user input, or continuous tasks.
* Prefer `for` when iterating over known collections or ranges.
