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
* **Important:** This single-line version only works if that line returns the promised value. Multi-line functions need explicit `return` statements.

### Expanded Example with Explicit Return

```swift
func pythagoras(a: Double, b: Double) -> Double {
    let input = a * a + b * b
    let root = sqrt(input)
    return root
}
```

* Both versions are valid. The single-line version works when the whole line returns the result.

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
* **Single-line functions can omit `return`** if that line returns the result.
* **Case sensitivity** applies.

## ✅ Summary

* Functions are reusable code blocks.
* Define with `func`, name, optional parameters, and a code block.
* Use `->` and `return` to send data back.
* Swift enforces order and naming of parameters.
* Functions can exit early using `return`.
* Data created inside is destroyed when done.
* Remember: **Single-line functions can omit `return`**, but multi-line ones require explicit `return` statements.

---

# Swift Functions: Returning Multiple Values with Tuples

## 🔤 Single Return Value Example

```swift
func isUppercase(string: String) -> Bool {
    string == string.uppercased()
}
```

* Compares a string to its uppercased version.
* Returns true if they match (string is fully uppercase), else false.

## 🔢 Returning Multiple Values with Arrays (Not Recommended)

```swift
func getUser() -> [String] {
    ["Taylor", "Swift"]
}

let user = getUser()
print("Name: \(user[0]) \(user[1])")
```

* Hard to track element meanings and prone to errors.

## 🔑 Using Dictionaries for Multiple Values (Also Not Ideal)

```swift
func getUser() -> [String: String] {
    ["firstName": "Taylor", "lastName": "Swift"]
}

let user = getUser()
print("Name: \(user["firstName", default: "Anonymous"]) \(user["lastName", default: "Anonymous"])")
```

* Keys are strings, need default values, prone to typos.

## ✅ Returning Multiple Values with Tuples (Recommended)

```swift
func getUser() -> (firstName: String, lastName: String) {
    (firstName: "Taylor", lastName: "Swift")
}

let user = getUser()
print("Name: \(user.firstName) \(user.lastName)")
```

* Provides named, type-safe values.
* Guaranteed presence and no need for default values.

### Access by Index (Less Preferred)

```swift
func getUser() -> (String, String) {
    ("Taylor", "Swift")
}

let user = getUser()
print("Name: \(user.0) \(user.1)")
```

### Destructuring Tuples

```swift
let (firstName, lastName) = getUser()
print("Name: \(firstName) \(lastName)")
```

* Shorthand for pulling values into individual constants.
* Use `_` to ignore parts of the tuple:

```swift
let (firstName, _) = getUser()
print("Name: \(firstName)")
```

## 🏆 Summary

* **Arrays** and **dictionaries** can store multiple values but have limitations.
* **Tuples** provide named, type-safe, and fixed-size collections of values.
* Tuples avoid default value issues and typos.
* Use **destructuring** for convenient extraction of tuple elements.
* Swift guarantees presence of tuple elements and types.

---

# Swift Functions: Customizing Parameter Labels

## 🧠 Key Concepts

* **External parameter names** are used at the function call site.
* **Internal parameter names** are used inside the function.
* Swift lets you control both for clearer, more natural code.

## 🔤 Example: Rolling Dice with Parameter Labels

```swift
func rollDice(sides: Int, count: Int) -> [Int] {
    var rolls = [Int]()
    for _ in 1...count {
        let roll = Int.random(in: 1...sides)
        rolls.append(roll)
    }
    return rolls
}

let rolls = rollDice(sides: 6, count: 4)
```

* Call site reads clearly: `rollDice(sides: 6, count: 4)`.

# Swift Functions: Customizing Parameter Labels

## 📝 Omitting External Parameter Names with \_

When you use `_` as an external parameter name, Swift omits the label at the call site. This is common in functions where the purpose of the parameter is obvious.

### Example: Checking Uppercase

```swift
func isUppercase(_ string: String) -> Bool {
    string == string.uppercased()
}

let result = isUppercase("HELLO, WORLD")
```

### Example: Appending to an Array

```swift
var items = ["Apple", "Banana"]
func addItem(_ item: String) {
    items.append(item)
}

addItem("Orange")
```

### Example: Printing a Message

```swift
func printMessage(_ message: String) {
    print(message)
}

printMessage("Hello, Swift!")
```

### Example: Calculating Square

```swift
func square(_ number: Int) -> Int {
    number * number
}

let squared = square(5)
print(squared) // 25
```

### Example: Checking for Even Numbers

```swift
func isEven(_ number: Int) -> Bool {
    number % 2 == 0
}

let result = isEven(8) // true
```


* `_` helps remove redundancy in function calls.
* Use for simple, clear functions where parameter intent is obvious.

## 📝 Customizing Labels for Natural Language

```swift
func printTimesTables(for number: Int) {
    for i in 1...12 {
        print("\(i) x \(number) is \(i * number)")
    }
}

printTimesTables(for: 5)
```

* `for` used as the external name, `number` as internal.
* Makes call site read naturally.

## 🛠 Syntax Summary

* **Two names**: `func functionName(external internal: Type)`

  * External name for the call site.
  * Internal name for use inside the function.
* **\_**: `func functionName(_ internal: Type)`

  * Removes external name.

## 🚀 Benefits

* Enhances **readability**.
* Makes code more **natural** to read and maintain.
* Clarifies intent at call site and inside the function.

## ✅ Example Recap

* `isUppercase(_:)` – removes external name.
* `printTimesTables(for:)` – custom external name for natural language.
* `rollDice(sides:count:)` – default external/internal names.

