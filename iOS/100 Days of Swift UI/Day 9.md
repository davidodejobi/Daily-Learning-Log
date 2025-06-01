# Closures in Swift – A Detailed, Beginner‑Friendly Guide

Closures are *anonymous functions*—self‑contained blocks of code you can treat like data: store in variables, pass as arguments, or return from other functions.  Think of them as **inline functions** that unlock concise, flexible code.  You’ll meet them everywhere in SwiftUI.

---

## 1.  Functions vs. Closures

| Feature                     | Regular Function (`func`)                       | Closure Expression (`{ }`)       |
| --------------------------- | ----------------------------------------------- | -------------------------------- |
| Has a name?                 | Yes (`greetUser`)                               | Optional (often none)            |
| Syntax                      | Outside braces, you list parameters/return type | Inside braces before `in`        |
| Can be stored in variables? | Yes (by name)                                   | Yes (the closure *is* the value) |

### Copying a Function

```swift
func greetUser() {
    print("Hi there!")
}

var greetCopy = greetUser  // no () – storing function itself

greetUser()   // Hi there!
greetCopy()   // Hi there! (same code)
```

*Parentheses **call** a function; leaving them off **stores** it.*

---

## 2.  Creating a Closure Literal

```swift
let sayHello = {
    print("Hi there!")      // body
}

sayHello()                  // runs later
```

* No parameters, no return → empty `()` and `Void` are implied.

### With Parameters & Return Value

```swift
let greet = { (name: String) -> String in
    "Hello, \(name)!"      // single expression → implicit return
}

print(greet("Taylor"))      // Hello, Taylor!
```

* Everything before `in` is the *signature*; after `in` is the body.

---

## 3.  Function *Types*

A function/closure’s type is `(ParameterTypes) -> ReturnType`.

```swift
var greetCopy: () -> Void = greetUser   // no params, no return

func getUserData(for id: Int) -> String { … }
let fetch: (Int) -> String = getUserData // label `for` disappears
print(fetch(1989))
```

> External parameter names are *not* part of the type.

---

## 4.  Passing Closures to Functions (Higher‑Order)

### Custom Sorting Example

```swift
let team = ["Gloria", "Suzanne", "Piper", "Tiffany", "Tasha"]

func captainFirst(_ a: String, _ b: String) -> Bool {
    if a == "Suzanne" { return true }
    if b == "Suzanne" { return false }
    return a < b
}

let sorted1 = team.sorted(by: captainFirst)
```

#### Inline Closure Instead of Separate Function

```swift
let sorted2 = team.sorted(by: { (a, b) -> Bool in
    if a == "Suzanne" { return true }
    if b == "Suzanne" { return false }
    return a < b
})
```

Same behavior, no standalone `func` needed.

---

## 5.  Syntax Shortcuts (Sugar)

1. **Type Inference** – Swift knows `a` & `b` are `String`, and return is `Bool`.
2. **Implicit `return`** – allowed for single‑expression closures.
3. **Shorthand Arguments** – `$0`, `$1`, … reference parameters in order.
4. **Trailing Closure** – if closure is last parameter, drop `by:` label and closing `)`.

```swift
let sorted3 = team.sorted {             // trailing closure
    if $0 == "Suzanne" { true }
    else if $1 == "Suzanne" { false }
    else { $0 < $1 }
}
```

---

## 6.  Capturing Values

Closures “close over” variables from their surrounding scope.

```swift
func makeCounter() -> () -> Int {
    var total = 0
    return {
        total += 1       // captures & mutates outer `total`
        return total
    }
}
let counter = makeCounter()
print(counter()) // 1
print(counter()) // 2
```

`total` lives on **inside** the closure even after `makeCounter()` returns.

---

## 7.  Escaping Closures

* Default: **non‑escaping** – runs before the surrounding function returns.
* Mark with `@escaping` if it may run *later* (e.g. asynchronous tasks).

```swift
func fetchData(completion: @escaping (Data?) -> Void) { … }
```

Remember to use `[weak self]` inside escaping closures to avoid retain cycles.

---

## 8.  Closures in SwiftUI (Why They Matter)

| SwiftUI Construct                  | Closure Role                    |
| ---------------------------------- | ------------------------------- |
| `Button("Tap") { … }`              | Action to run on tap            |
| `List(items) { item in … }`        | Row view builder                |
| `withAnimation { state.toggle() }` | Wraps state change in animation |

SwiftUI relies on closures to express *behavior* directly alongside UI structure.

---

## 🏁 Key Takeaways

1. **Closure = function value** you can treat like data.
2. Use closures to customize APIs (`sorted`, `map`, SwiftUI views).
3. Learn the shorthand: `$0`, implicit return, trailing closure – it’s everywhere.
4. Closures capture variables, enabling patterns like counters or state mutations.
5. SwiftUI’s declarative syntax is closure‑driven – mastering closures unlocks SwiftUI.

Practice: convert the custom sort function into:

* Full closure literal.
* Trailing‑closure form with `$0`/`$1`.

