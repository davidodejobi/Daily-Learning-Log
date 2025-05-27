# Swift Checkpoint Practice: Integer Square Root Function

## 🚀 Practice Challenge

### 📌 Detailed Problem Statement

You need to write a **Swift function** that takes an integer between **1 and 10,000**, and returns the integer square root of that number. However, there are specific rules you must follow:

* **No using Swift’s built-in `sqrt()` or similar functions.** You need to calculate the square root yourself.
* The function should only return the **integer square root**. For example, the square root of 9 is 3 (since 3 × 3 = 9), and the square root of 25 is 5. You should not return decimal square roots.
* If the input number is **less than 1** or **greater than 10,000**, your function should **throw an error** named `outOfBounds`.
* If the number does not have an integer square root (e.g., 3, 8, etc.), your function should **throw an error** named `noRoot`.

### 🔍 Additional Hints:

* This problem can be solved using a **brute force** approach.
* Loop through integers from 1 up to 100 (since the square root of 10,000 is 100) and check whether their square matches the input.
* If you complete the loop without finding an integer square root, throw `noRoot`.
* You can define separate out of bounds errors for numbers too small or too large, but a general `outOfBounds` is fine.

### 🧠 Challenge:

* Define the `Error` enum to handle `outOfBounds` and `noRoot` errors.
* Write a **throwing function** to calculate the integer square root.
* Implement **error handling** when calling the function.

<details><summary>✅ Show Solution</summary>

```swift
enum RootError: Error {
    case outOfBounds, noRoot
}

func integerSquareRoot(of number: Int) throws -> Int {
    if number < 1 || number > 10_000 {
        throw RootError.outOfBounds
    }
    for i in 1...100 {
        if i * i == number {
            return i
        }
    }
    throw RootError.noRoot
}

// Example usage
let testNumbers = [25, 26, 10_000, 0, 10001]
for num in testNumbers {
    do {
        let root = try integerSquareRoot(of: num)
        print("The integer square root of \(num) is \(root)")
    } catch RootError.outOfBounds {
        print("Number \(num) is out of bounds.")
    } catch RootError.noRoot {
        print("No integer square root for \(num).")
    } catch {
        print("An unexpected error occurred.")
    }
}
```

</details>

Would you like me to prepare **more checkpoint practice questions** or move on to **inout parameters**?
