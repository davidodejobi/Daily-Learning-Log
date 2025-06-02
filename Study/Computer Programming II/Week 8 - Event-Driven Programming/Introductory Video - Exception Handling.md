# Week 8: Introduction to Exception Handling – Part 1

## 🎯 Learning Objectives

* Understand what **exceptions** are and why they matter.
* Learn the basic control flow: **try / catch / finally** (or equivalent).
* Recognise the advantages of exceptions over ad‑hoc `if‑else` error checks.

---

## 1  Why Exception Handling?

Real programs encounter unexpected situations:

* Invalid user input (e.g. entering text instead of a number)
* Missing files or database records
* Divide‑by‑zero, arithmetic overflow
* Network time‑outs or server errors

Without structured handling, such errors crash the application or corrupt data. **Exception handling** lets us detect, report, and, when possible, recover gracefully.

---

## 2  Core Terminology

| Term                     | Meaning                                                                    |
| ------------------------ | -------------------------------------------------------------------------- |
| **Exception**            | A runtime signal (often an object) indicating something abnormal happened. |
| **Throw / Raise**        | Create and propagate an exception.                                         |
| **Try Block**            | Code that should run normally.                                             |
| **Catch / Except Block** | Code that handles a specific exception type.                               |
| **Finally Block**        | Code that always executes (cleanup).                                       |

---

## 3  Typical Control Flow

```text
try {
    // normal code
    •••
    if (error) throw Exception;
}
catch (ExceptionType e) {
    // handle / log / recover
}
finally {
    // always runs (optional)
}
```

---

## 4  Why Not Just `if … else` Everywhere?

* Scattering error checks muddies the main logic ("spaghetti code").
* Hard to forward errors up multiple call levels.
* Exceptions **unwind the call stack automatically** and centralise handling.

---

## 5  Real‑World Analogy

**Booking a flight online**

* **Normal path:** choose flight → pay → ticket issued.
* **Exception:** credit‑card declined. The payment module *throws* an exception. A handler prompts the user for another card or aborts cleanly, rather than crashing mid‑transaction.

---

## 6  Language Syntax Snapshot

| Language   | Throwing                           | Handling                                             |
| ---------- | ---------------------------------- | ---------------------------------------------------- |
| **C++**    | `throw std::runtime_error("msg");` | `try { … } catch (const std::exception& e) { … }`    |
| **Java**   | `throw new IOException("msg");`    | `try { … } catch(IOException e) { … } finally { … }` |
| **Python** | `raise ValueError("msg")`          | `try: … except ValueError as e: … finally: …`        |

---

## 7  Advantages of Using Exceptions

1. **Seamless error handling** – Detect and handle errors without scattering `if/else` checks.
2. **Improved readability & maintainability** – Main logic stays clear; error logic is isolated in `catch` blocks.
3. **Enhanced user experience** – Programs fail gracefully with friendly messages instead of crashing.
4. **Error isolation & localization** – Handlers can be placed near where errors occur, preventing ripple effects.
5. **Flexibility** – Decide at runtime to retry, log, propagate, or convert errors.
6. **Separation of concerns** – Core logic focuses on intended tasks; exception code handles the unexpected.

## 8  Key Takeaways (so far)

* An **exception** is a structured, language‑supported error signal.
* **try / catch / finally** blocks separate normal logic from error logic.
* Using exceptions improves readability, reliability, and error propagation.

## 8  Advanced Topics (Part 2)

The second half of the video dives deeper into practical techniques.

### 8.1 Multiple `catch` Blocks

Handle specific exceptions first, then a generic fallback.

```cpp
try {
    risky();
}
catch (const FileNotFound& e) {
    // specific recovery
}
catch (const std::exception& e) {
    // generic fallback
}
```

### 8.2 Custom Exception Classes

Create meaningful types to convey context.

```cpp
class InvalidAge : public std::runtime_error {
public:
    InvalidAge(int age) : runtime_error("Age out of range"), age_(age) {}
    int age() const { return age_; }
private:
    int age_;
};
```

Throw with `throw InvalidAge(inputAge);` and catch explicitly.

### 8.3 Rethrowing Exceptions

Sometimes a lower‑level handler logs or cleans up, then rethrows up the stack:

```cpp
catch (...) {
    logError();
    throw;   // preserve original type
}
```

### 8.4 Stack Unwinding & RAII

As an exception propagates, C++ automatically calls destructors for local objects. Use RAII wrappers (e.g., `std::lock_guard`) to release resources safely.

### 8.5 `finally` Patterns in C++

C++ lacks a `finally` keyword, but RAII achieves the same; in C++23 `try { … } finally { … }` will exist.

### 8.6 Checked vs Unchecked Exceptions (Java)

* **Checked** (IOExceptions) must be declared/handled.
* **Unchecked** (RuntimeExceptions) can propagate freely.
  Choose wisely—overchecking clutters code.

### 8.7 Exception Safety Levels

| Level        | Guarantee                                 |
| ------------ | ----------------------------------------- |
| **No‑throw** | Operation never throws (e.g., swap).      |
| **Strong**   | If it throws, program state is unchanged. |
| **Basic**    | Invariants hold, but state may change.    |

### 8.8 Best Practices Recap

1. **Throw by value, catch by (const) reference** (C++).
2. Never throw from a destructor during stack unwinding.
3. Prefer specific exceptions over generic ones.
4. Use RAII or `finally` to release resources.
5. Log exceptions with sufficient context.

---

## 📌 Final Takeaways

* Exception handling is essential for robust, fault‑tolerant software.
* Advanced features (custom types, rethrowing, RAII) let you build safe, maintainable systems.
* Always balance clarity, performance, and safety when designing error paths.

