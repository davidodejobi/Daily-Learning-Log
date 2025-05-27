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

# Swift Functions: Handling Errors Gracefully

## 🧠 Key Concepts

* Functions can **throw errors** to indicate failure.
* Errors are defined using an **enum** that conforms to the `Error` protocol.
* Functions that might throw must be marked with `throws`.
* Use `do`, `try`, and `catch` to handle thrown errors.

## 🔤 Defining Possible Errors

```swift
enum PasswordError: Error {
    case short, obvious
}
```

* Defines two potential password errors: `short` and `obvious`.

## 🏗 Writing a Throwing Function

```swift
func checkPassword(_ password: String) throws -> String {
    if password.count < 5 {
        throw PasswordError.short
    }
    if password == "12345" {
        throw PasswordError.obvious
    }
    if password.count < 8 {
        return "OK"
    } else if password.count < 10 {
        return "Good"
    } else {
        return "Excellent"
    }
}
```

* `throws` indicates potential error throwing.
* Use `throw` to exit early with an error.
* Returns a rating string if no errors occur.

## ⚙️ Handling Errors with `do`, `try`, and `catch`

```swift
let string = "12345"

do {
    let result = try checkPassword(string)
    print("Password rating: \(result)")
} catch PasswordError.short {
    print("Please use a longer password.")
} catch PasswordError.obvious {
    print("I have the same combination on my luggage!")
} catch {
    print("There was an error.")
}
```

* `do` starts the block of potentially risky code.
* `try` calls the throwing function.
* `catch` handles all thrown errors; can specify cases.

## 🚨 Using `try!` (Use With Caution)

```swift
let result = try! checkPassword("12345")  // Crashes if error is thrown
```

* `try!` skips `do-catch`, crashing if an error occurs.
* Only use when you’re **sure** no errors can happen.

## 📝 Real-World Error Handling

* Apple's APIs use throwing functions extensively.
* Errors typically include localized descriptions.

```swift
catch {
    print(error.localizedDescription)
}
```

* Use this to display meaningful error messages to users.

## ✅ Summary

* Define potential errors with `enum` conforming to `Error`.
* Mark functions with `throws` if they might fail.
* Handle errors with `do-try-catch` or `try!` (with caution).
* Use `error.localizedDescription` for detailed error messages.

---

# Swift Functions: Summary of Key Concepts

## 📝 1. Defining and Calling Functions

```swift
func showWelcome() {
    print("Welcome to my app!")
}
showWelcome()
```

* Basic function with no parameters or return value.

## 📝 2. Function with Parameters

```swift
func printTimesTables(number: Int) {
    for i in 1...12 {
        print("\(i) x \(number) is \(i * number)")
    }
}
printTimesTables(number: 5)
```

* Accepts an integer parameter.

## 📝 3. Function with Multiple Parameters

```swift
func printTimesTables(number: Int, end: Int) {
    for i in 1...end {
        print("\(i) x \(number) is \(i * number)")
    }
}
printTimesTables(number: 5, end: 20)
```

* Multiple parameters for added flexibility.

## 📝 4. Single Return Value

```swift
func isUppercase(string: String) -> Bool {
    string == string.uppercased()
}
```

* Returns a Boolean indicating if the string is uppercase.

## 📝 5. Returning Multiple Values with Tuples

```swift
func getUser() -> (firstName: String, lastName: String) {
    (firstName: "Taylor", lastName: "Swift")
}
```

* Returns a tuple with multiple values.

## 📝 6. Default Parameter Values

```swift
func printTimesTables(for number: Int, end: Int = 12) {
    for i in 1...end {
        print("\(i) x \(number) is \(i * number)")
    }
}
printTimesTables(for: 8)  // Uses default end = 12
```

* Allows optional parameters with defaults.

## 📝 7. Omitting External Parameter Names

```swift
func isUppercase(_ string: String) -> Bool {
    string == string.uppercased()
}
```

* Removes external parameter name for cleaner calls.

## 📝 8. Custom External Parameter Names

```swift
func printTimesTables(for number: Int) {
    for i in 1...12 {
        print("\(i) x \(number) is \(i * number)")
    }
}
printTimesTables(for: 5)
```

* Customizes parameter labels for natural language.

## 📝 9. Throwing Functions and Error Handling

```swift
enum PasswordError: Error {
    case short, obvious
}

func checkPassword(_ password: String) throws -> String {
    if password.count < 5 { throw PasswordError.short }
    if password == "12345" { throw PasswordError.obvious }
    return "Good"
}

do {
    let result = try checkPassword("12345")
} catch {
    print("There was an error.")
}
```

* Handles errors using `throws`, `do`, `try`, and `catch`.

## 🏆 Summary

* **Functions** are building blocks for reusable code.
* Use **parameters** for customization.
* Use **return values** for computed data.
* Use **tuples** for multiple return values.
* **Default values** simplify calls.
* **Custom and omitted parameter names** improve clarity.
* **Error handling** makes functions robust.

