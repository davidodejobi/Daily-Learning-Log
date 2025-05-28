# Worksheet – Recursive Algorithms

Below is a breakdown of each worksheet item with the **correct answer** and a brief explanation so you can review quickly.

---
## 1  True/False Questions

| #  | Statement                                                                                                                       | Answer | Why?                                                                                                 |
| -- | ------------------------------------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------------------------------------------------------------------- |
| 1  | Recursion is a programming technique where a function calls itself.                                                             | **T**  | That’s the definition of direct recursion.                                                           |
| 2  | A recursive function must have a base case to stop the recursion.                                                               | **T**  | Without a base case, the calls never end (stack overflow).                                           |
| 3  | Any recursive function using a list can be adjusted to use a set.                                                               | **F**  | Lists are ordered and may contain duplicates; sets are unordered/unique—algorithm may rely on order. |
| 4  | Recursive functions are always more efficient than iterative solutions.                                                         | **F**  | Recursion adds call‑stack overhead; iteration is often faster.                                       |
| 5  | Recursive functions can be called with different parameters in each recursive call.                                             | **T**  | Each call typically modifies the argument to move toward the base case.                              |
| 6  | A recursive function can have multiple base cases.                                                                              | **T**  | E.g., Fibonacci has two base cases (n ≤ 1).                                                          |
| 7  | Recursive functions can only call themselves once within their body.                                                            | **F**  | Many algorithms (e.g., Fibonacci, quicksort) call themselves multiple times.                         |
| 8  | Recursion is the only way to implement functions that solve certain mathematical problems efficiently, such as factorials.      | **F**  | Factorial can be computed iteratively just as efficiently.                                           |
| 9  | If function A calls function B, and B calls A, then neither function is recursive because they do not directly call themselves. | **F**  | This is **mutual recursion**—still recursion.                                                        |
| 10 | Recursion always leads to infinite recursive calls if not implemented correctly.                                                | **T**  | A missing/incorrect base case causes infinite recursion and stack overflow.                          |
| 11 | Recursion is generally recommended for problems that can be easily solved using loops.                                          | **F**  | For simple loopable problems, iteration is preferred for efficiency.                                 |
| 12 | Recursive functions in Python cannot be optimised for better performance.                                                       | **F**  | Memoization, caching, and algorithm tweaks can optimise recursive Python code.                       |

---

## 2  Multiple‑Choice Questions

### Q2.  Role of the Base Case

> **Correct answer:** **C** – “To define the initial condition that stops the recursive calls.”
> **Why:** The base case prevents infinite recursion and begins the unwind phase.

### Q3.  Recursion vs Iteration Comparison

> **Correct answer:** **D** – “Recursion and iteration are different techniques with their own strengths and weaknesses, although they can be used interchangeably.”
> **Why:** Neither technique is universally superior; choice depends on the problem.

### Q4.  Main Benefit of Using Recursion

> **Correct answer:** **C** – “Recursion can solve complex problems concisely by breaking them down into smaller instances.”
> **Why:** Recursion mirrors self‑similar structures, often yielding shorter, clearer code.

### Q5.  Potential Downside of Recursion

> **Correct answer:** **A** – “Recursion can lead to infinite function calls and stack overflow errors.”
> **Why:** Without a correct base case or with excessive depth, recursion exhausts the call stack.

---

### Key Takeaway

Recursion is powerful for self‑similar or divide‑and‑conquer problems, but always weigh readability against overhead and ensure a sound base case.
