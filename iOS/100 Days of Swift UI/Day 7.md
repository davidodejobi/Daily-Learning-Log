# Swift Functions: Creating Reusable Code

## 🧠 Key Concepts

* **Functions** are blocks of code that perform a specific task and can be reused.
* Functions help avoid repeating code and make it easier to maintain.
* In Swift, functions are defined using the `func` keyword.

## 🔤 Defining and Calling a Function

```swift
func showWelcome() {
    print("Welcome to my app!")
    print("By default This prints out a conversion")
    print("chart from centimeters to inches, but you")
    print("can also set a custom range if you want.")
}

showWelcome()  // Function call
```

## 🛠 Function Anatomy

* **func**: marks the start of a function.
* **Function Name**: like `showWelcome` to identify the function.
* **Parameters**: inside `()`, used to pass data (e.g., `number: Int`).
* **Braces {}**: enclose the code block of the function.
* **Return Type**: use `->` followed by a data type to specify what the function returns.

## 🔢 Parameters and Arguments

### Function with a Parameter

```swift
func printTimesTables(number: Int) {
    for i in 1...12 {
        print("\(i) x \(number) is \(i * number)")
    }
}

printTimesTables(number: 5)
```

* **Parameter**: `number` is a placeholder.
* **Argument**: `5` is the actual value passed.

### Multiple Parameters

```swift
func printTimesTables(number: Int, end: Int) {
    for i in 1...end {
        print("\(i) x \(number) is \(i * number)")
    }
}

printTimesTables(number: 5, end: 20)
```

## 🔁 Returning Values from Functions

### Basic Example

```swift
func rollDice() -> Int {
    Int.random(in: 1...6)
}

let result = rollDice()
print(result)
```

* `-> Int` indicates the function returns an Int.
* The function call receives and stores the returned value.

### Advanced Example

```swift
func areLettersIdentical(string1: String, string2: String) -> Bool {
    string1.sorted() == string2.sorted()
}

print(areLettersIdentical(string1: "abc", string2: "cab"))
```

* Compares if two strings contain the same letters, regardless of order.
* `-> Bool` ensures the function returns `true` or `false`.

### Pythagorean Theorem Example

```swift
func pythagoras(a: Double, b: Double) -> Double {
    sqrt(a * a + b * b)
}

let c = pythagoras(a: 3, b: 4)
print(c)  // 5.0
```

* Calculates the hypotenuse using Pythagoras' theorem.
* `sqrt()` returns the square root.

## 🚨 Early Return

* Use `return` by itself to exit a function early, e.g.:

```swift
func checkNumber(_ number: Int) {
    if number < 0 {
        print("Negative number detected.")
        return
    }
    print("Number is valid.")
}
```

## 🔀 Key Differences

* **Parameters**: placeholders in the function definition.
* **Arguments**: actual values passed at the call site.
* Swift enforces explicit naming and order of parameters.

## ⚠️ Common Points

* Data created inside a function **does not persist** outside.
* Functions make code **reusable** and **maintainable**.
* Functions can return values using `->` and `return`.
* **Case sensitivity** applies.

## ✅ Summary

* Functions are reusable code blocks.
* Define with `func`, name, optional parameters, and a code block.
* Use `->` and `return` to send data back.
* Swift enforces order and naming of parameters.
* Functions can exit early using `return`.
* Data created inside is destroyed when done.

Would you like me to now add **default parameter values** and **inout parameters**?
