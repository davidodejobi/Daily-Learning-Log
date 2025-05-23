# Kotlin Basics: Your First Program

> **Purpose of this Note**
> This guide walks absolute beginners through their first steps in Kotlin. Every example can be pasted directly into [Kotlin Playground](https://play.kotlinlang.org). Keep this note bookmarked—each section builds on the previous one, so you can return anytime and still follow along.

---

## 1  Why Learn Kotlin for Android?

Kotlin is Google’s preferred language for Android development because it offers:

| Benefit                         | Why it matters                                   |
| ------------------------------- | ------------------------------------------------ |
| **Concise syntax**              | Write less boilerplate; focus on features.       |
| **Null‑safety**                 | Catches many crashes at compile time.            |
| **100 % Java interoperability** | Re‑use the entire Java ecosystem.                |
| **Modern tooling**              | First‑class IDE support and a growing community. |

---

## 2  Required Tools for This Pathway

| Tool                       | Purpose                                                                |
| -------------------------- | ---------------------------------------------------------------------- |
| **Kotlin Playground**      | Browser‑based editor to experiment with Kotlin quickly.                |
| **Kotlin Compiler**        | Translates Kotlin source into bytecode; Playground calls this for you. |
| **Android Studio** (later) | Full IDE for building, running, and debugging Android apps.            |

---

## 3  Your First Kotlin Program

Paste the starter code inside the Playground and click **Run**:

```kotlin
fun main() {
    println("Hello, world!")
}
```

### What Just Happened?

1. **Compilation** – The compiler checked your syntax and produced bytecode.
2. **Execution** – The bytecode ran on the server; the console printed:

```
Hello, world!
```

---

## 4  Anatomy of a Kotlin Function

| Part       | Example | Meaning                                               |
| ---------- | ------- | ----------------------------------------------------- |
| Keyword    | `fun`   | Declares a function.                                  |
| Name       | `main`  | Identifier (should use *camelCase*, start lowercase). |
| Parameters | `()`    | Comma‑separated inputs—empty here.                    |
| Body       | `{ … }` | Instructions to run when the function is called.      |

> **Tip – Definition vs Call**
> • *Define* once, *call* as many times as needed.

```kotlin
fun addOne(n: Int) {          // definition
    println(n + 1)
}

fun main() {
    addOne(5)                 // call #1 → 6
    addOne(42)                // call #2 → 43
}
```

---

## 5  Modifying Output

Change the greeting by editing the argument to `println()`:

```kotlin
fun main() {
    println("Hello, Android!")
}
```

Run it →

```
Hello, Android!
```

### 5.1  Printing Multiple Lines

Add a second statement on a **new line** inside the function body:

```kotlin
fun main() {
    println("Hello, Android!")
    println("Hello, Android!")
}
```

Output:

```
Hello, Android!
Hello, Android!
```

Try changing the message to include your own name:

```kotlin
println("Hello, David!")
```

---

## 6  Kotlin Style Guide Essentials

Follow Google’s [Kotlin style guide](https://developer.android.com/kotlin/style-guide) to keep code readable and consistent.

| Rule                                | Example                             |
| ----------------------------------- | ----------------------------------- |
| **Camel‑case function names**       | `calculateTip()` not `CalculateTip` |
| **One statement per line**          | No semicolons needed at EOL.        |
| **Brace position**                  | `fun foo() {` (space before `{`).   |
| **Indent with 4 spaces**            | Avoid tabs.                         |
| **Closing brace aligns with `fun`** | See examples above.                 |

---

## 7  Troubleshooting Syntax Errors

Even experts mistype symbols. The compiler will point to the first place it gets confused.

### Example Error

```kotlin
fun main() {
    println("Today is sunny!)
}
```

Playground shows *Expecting '"'* and *Expecting ')'*
**Fix:** add the missing closing quote **before** the parenthesis.

```kotlin
fun main() {
    println("Today is sunny!")
}
```

Run again → no errors, desired output appears.

> **Debugging mindset**: Read error messages top‑to‑bottom, check spelling, quotes, parentheses, and braces.

---

## 8  Practice Exercises

Work these directly in Kotlin Playground.

1. **Predict the Output**
   What appears in the console?

   ```kotlin
   fun main() {
       println("1")
       println("2")
       println("3")
   }
   ```

2. **Vertical Cheer**
   Write a program that outputs:

   ```
   I'm
   learning
   Kotlin!
   ```

3. **Weekdays Sorted**
   Start from:

   ```kotlin
   fun main() {
       println("Tuesday")
       println("Thursday")
       println("Wednesday")
       println("Friday")
       println("Monday")
   }
   ```

   Rearrange the statements so the days print in order Monday → Friday.

4. **Find & Fix the Bug**
   Each snippet compiles with an error; correct it.

   ```kotlin
   fun main() {
       println("Tomorrow is rainy")
   }
   ```

   ```kotlin
   fun main() {
       printLine("There is a chance of snow")
   }
   ```

   ```kotlin
   fun main() {
       println("Cloudy") println("Partly Cloudy") println("Windy")
   }
   ```

   ```kotlin
   fun main() (
       println("How's the weather today?")
   )
   ```

> **Solutions** – Peek only after you’ve tried: scroll to the end of this note.

---

## 9  Key Takeaways

* Every Kotlin program starts in `main()`.
* Use `fun` + *camelCaseName* + `()` + `{}` to define functions.
* `println()` sends text to standard output, one line at a time.
* Follow the style guide for braces, spacing, and naming.
* Errors are normal—learn to read the compiler’s hints.

---

## 10  Next Steps

Continue to the **Variables & Data Types** codelab to store information in memory and create more dynamic programs.

---

## Appendix – Exercise Solutions

<details>
<summary>Click to reveal</summary>

### Exercise 1

Console prints exactly what is inside each `println()`:

```
1
2
3
```

### Exercise 2

```kotlin
fun main() {
    println("I'm")
    println("learning")
    println("Kotlin!")
}
```

### Exercise 3 (Weekdays)

```kotlin
fun main() {
    println("Monday")
    println("Tuesday")
    println("Wednesday")
    println("Thursday")
    println("Friday")
}
```

### Exercise 4 Bug Fixes

```kotlin
// 4‑a – Missing brace fixed
fun main() {
    println("Tomorrow is rainy")
}

// 4‑b – Incorrect function name → println
fun main() {
    println("There is a chance of snow")
}

// 4‑c – One statement per line
fun main() {
    println("Cloudy")
    println("Partly Cloudy")
    println("Windy")
}

// 4‑d – Parentheses vs braces
fun main() {
    println("How's the weather today?")
}
```

</details>

## Learn More

- [Hello World](https://play.kotlinlang.org/byExample/01_introduction/01_Hello%20world)
- [Program entry point](https://kotlinlang.org/docs/basic-syntax.html#program-entry-point)
- [Print to the standard output](https://kotlinlang.org/docs/basic-syntax.html#print-to-the-standard-output)
- [Basic syntax of functions](https://kotlinlang.org/docs/basic-syntax.html#functions)
- [Keywords and operators](https://kotlinlang.org/docs/keyword-reference.html)
- [Functions Concept](https://kotlinlang.org/docs/functions.html)
- [println](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.io/println.html)
- [Kotlin style guide](https://developer.android.com/kotlin/style-guide)

