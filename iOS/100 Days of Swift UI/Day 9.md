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

## 🏁 Key Takeaways

1. **Closure = function value** you can treat like data.
2. Use closures to customize APIs (`sorted`, `map`, SwiftUI views).

---

# Swift Closures – Reducing Syntax Clutter

This guide walks through *every* simplification step, explaining **why** the syntax works and **when** to use each trick.

---

## 🚀 Starting Point – Why It Feels Verbose

```swift
let captainFirstTeam = team.sorted(by: { (name1: String, name2: String) -> Bool in
    if name1 == "Suzanne" { return true }
    if name2 == "Suzanne" { return false }
    return name1 < name2
})
```

*Pain points*

1. **Type clutter** – `String`, `Bool` appear although Swift can guess.
2. **Label + parentheses** – `by:` and the wrapping `()` obscure the logic.
3. **Explicit names** – `name1`, `name2` are repeated, yet the relationship is obvious: “first vs. second”.

We’ll trim these one-by-one.

---

## 1️⃣  Type Inference – Let Swift Do the Guessing

### What happens?

* Swift knows `team` is `[String]` → `sorted(by:)` must receive `(String, String) -> Bool`.
* Therefore it can infer each parameter’s type (String) **and** the return type (Bool).

```swift
let captainFirstTeam = team.sorted(by: { name1, name2 in
    // Types inferred: name1:String  name2:String  -> Bool
    if name1 == "Suzanne" { return true }
    if name2 == "Suzanne" { return false }
    return name1 < name2
})
```

**Why it’s safe**: If you accidentally return a non-Bool, the compiler still warns you – inference only removes *boilerplate*, not safety.

---

## 2️⃣  Trailing-Closure Syntax – Yank the Label

### Rule of thumb

> When the *last* parameter is a closure, you can move it **outside** the parentheses and drop the label.

```swift
let captainFirstTeam = team.sorted { name1, name2 in
    …
}
```

*Visual benefit*: The algorithm sits flush under `sorted`, easier to scan.

> **Tip**: If the method has *only* a closure, you can also drop the empty `()` entirely: `dispatch { … }`.

---

## 3️⃣  Shorthand Argument Names (`$0`, `$1`)

### Why `$0`?

* Inside a closure, if you omit a parameter list, Swift auto-creates **positional vars**: `$0`, `$1`, `$2` … .
* Great when **each value is used once** and their *roles are obvious*.

```swift
let captainFirstTeam = team.sorted {
    if $0 == "Suzanne" { true }
    else if $1 == "Suzanne" { false }
    else { $0 < $1 }
}
```

> **Read aloud**: “Sort so that **\$0** comes before **\$1** when `$0` is Suzanne…”

### When to *avoid* shorthand

| Situation                  | Better Alternative           |
| -------------------------- | ---------------------------- |
| Long closure body          | Use named params for clarity |
| Same param used many times | Names reduce mental mapping  |
| ≥3 params (\$2, \$3)       | Prefer explicit names        |

---

## 4️⃣  Single-Expression Closures – Implicit `return`

If the body is **one line**, Swift assumes it should be returned.

```swift
let reverseTeam = team.sorted { $0 > $1 }   // reverse order
```

No `return`, no braces around an if/else – micro & readable.

---

## 5️⃣  Quick Tour of Higher-Order Helpers

### `filter(_:)` – keep items that pass a test

```swift
let tPlayers = team.filter { $0.hasPrefix("T") }
// ["Tiffany", "Tasha"]
```

*Closure receives each element; returns Bool.*

### `map(_:)` – transform each item, return new array

```swift
let badgeNames = team.map { "★ " + $0.uppercased() }
// ["★ GLORIA", …]
```

*Return type can differ – e.g., `[String]` → `[Image]` in SwiftUI.*

---

## 6️⃣  Why This Matters for SwiftUI

| SwiftUI Call                        | Under-the-hood Closure                               |
| ----------------------------------- | ---------------------------------------------------- |
| `Button { sendEmail() }`            | Action closure executed on tap                       |
| `List(users) { user in Row(user) }` | Row-builder closure creating a view for each element |
| `VStack { Text("A"); Text("B") }`   | Closure returning a stack’s children                 |
| `withAnimation { isOpen.toggle() }` | Closure holding a state change to animate            |

Mastering this syntax lets you **read & write SwiftUI fluently** – most view builders are nothing more than trailing closures.

---

## 🏁 Consolidated Cheat-Sheet

1. **Infer types** – delete `(Type)` & `-> Return` when compiler can guess.
2. **Use trailing closure** if last parameter is a closure.
3. **Single line?** Drop `return`.
4. **Consider `$0` / `$1`** for tiny, one-shot comparisons.
5. **Prefer names** when code grows or arguments repeat.
6. **Write verbose first → refactor** – let compiler guide you.

> **Challenge**: Rewrite a verbose `filter` that removes empty strings from an array

---

# Accepting Functions (Closures) as Parameters – In‑Depth Guide

Passing a function into another function lets you **inject custom behavior** at call‑time.  This pattern powers the standard library (`sorted`, `map`, `filter`), async APIs (`URLSession` callbacks), and nearly every SwiftUI view builder.

---

## 1️⃣  Function Values Recap

```swift
func greetUser() {
    print("Hi there!")
}

var greetCopy: () -> Void = greetUser   // store the *function value*

// greetCopy is now a variable you can call later
greetCopy()      // Hi there!
```

*Type signature* `() -> Void` means **no parameters, no return**.

> **Rule:** A function’s *value* is written as `(ParamTypes) -> ReturnType`.

---

## 2️⃣  Single Function Parameter

### Example: Building an Array with a Generator

```swift
func makeArray(size: Int,
               using generator: () -> Int) -> [Int] {
    var numbers: [Int] = []
    for _ in 0..<size {
        numbers.append(generator())   // call the passed‑in function
    }
    return numbers
}
```

**Signature dissection**

| Part                         | Meaning                                                |
| ---------------------------- | ------------------------------------------------------ |
| `size: Int`                  | how many values to generate                            |
| `using generator: () -> Int` | *parameter is itself a function* that returns an `Int` |
| `-> [Int]`                   | `makeArray` returns an array of integers               |

#### Invoking – Two Styles

| Trailing‑Closure                  | Named Function |
| --------------------------------- | -------------- |
| \`\`\`swift                       |                |
| let rolls = makeArray(size: 10) { |                |

```
Int.random(in: 1...6)
```

}
`|`swift
func d6() -> Int { Int.random(in: 1...6) }
let rolls = makeArray(size: 10, using: d6)

````|

> **Trailing closure rule**: If the *last* parameter is a closure, you may drop the label and outside parentheses.

---
## 3️⃣  Function Parameters *with Inputs & Outputs*
You can accept complex closures just by changing the type.

### Example: Custom Validator
```swift
func validate(_ value: String,
             with rule: (String) -> Bool) -> Bool {
    rule(value)          // returns true/false based on custom rule
}

let isEmail = { str in str.contains("@") }
print(validate("hello@site.com", with: isEmail)) // true
````

*`rule`* takes one `String`, returns `Bool`.

---

## 4️⃣  Multiple Closure Parameters + Trailing Syntax

Swift allows **multiple** trailing closures by naming each subsequent closure.

```swift
func doImportantWork(first: () -> Void,
                     second: () -> Void,
                     third: () -> Void) {
    print("Start 1"); first()
    print("Start 2"); second()
    print("Start 3"); third()
}

doImportantWork {
    print("🏁 First")
} second: {
    print("🏁 Second")
} third: {
    print("🏁 Third")
}
```

SwiftUI example:

```swift
Section {
    Text("Rows…")
} header: {
    Text("Header")
} footer: {
    Text("Footer")
}
```

---

## 5️⃣  Escaping vs. Non‑Escaping Parameters

* **Non‑escaping** (default): closure must finish before the host function returns.
* **@escaping**: closure may run *later* (async work). Captures of `self` must be `[weak self]` to avoid retain cycles.

```swift
func fetchJSON(from url: URL,
              completion: @escaping (Data?) -> Void) {
    URLSession.shared.dataTask(with: url) { data, _, _ in
        completion(data)   // runs later → escaping
    }.resume()
}
```

---

## 6️⃣  Autoclosure – Lazily Wrap an Expression

`@autoclosure` lets callers pass *expressions* that become closures.

```swift
func assert(_ condition: @autoclosure () -> Bool,
            _ message: String) {
    if !condition() { print("Assertion failed: \(message)") }
}
assert(2 + 2 == 4, "Math broke!")  // expression auto‑wrapped
```

---

## 7️⃣  Practical Patterns in SwiftUI

| Pattern                                                  | Function Parameters                 |
| -------------------------------------------------------- | ----------------------------------- |
| `Button(action:label:)`                                  | `( () -> Void, () -> some View )`   |
| `List(data,rowContent:)`                                 | `(Data, (Data.Element) -> RowView)` |
| `animation(_:value:)`                                    | `(Animation, () -> Value)`          |
| Mastering function parameters = effortless SwiftUI APIs. |                                     |

---

## 🏁 Cheat‑Sheet

1. **Type**: `(InputTypes) -> ReturnType`.
2. **Trailing closure** eliminates label and `()` when closure is last.
3. **Multiple closures** → keep first trailing, label the rest.
4. **@escaping** for async; use `[weak self]` as needed.
5. **@autoclosure** wraps an expression for lazy eval.
6. Start verbose → refactor: remove types, add trailing syntax, consider `$0`.

> **Challenge**: Write a `repeatTask(times:task:)` that executes a closure *n* times and measure its duration.
