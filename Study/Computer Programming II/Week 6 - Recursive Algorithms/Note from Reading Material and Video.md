# Week 6: Recursive Algorithms and Their Applications – Detailed Summary

## 🎯 Learning Objectives

* Recognize problems well‑suited to recursion.
* Implement basic recursive functions in C++.
* Compare recursion with iteration in terms of readability, performance, and memory use.
* Identify drawbacks such as stack‑overflow risk and function‑call overhead.

---

## 1  What Is Recursion?

Recursion is a problem‑solving technique in which a function calls **itself** to break a complex task into smaller, self‑similar sub‑tasks. Each recursive function must include:

1. **Base case** – stops further calls.
2. **Recursive step** – reduces the problem toward the base case.

### 1.1 Analogy

> A set of Russian nesting dolls: to reach the smallest doll you repeatedly open a slightly smaller one. Similarly, each recursive call opens a smaller sub‑problem until the simplest (base) case is reached.

---

## 2  Recursion vs Iteration

| Feature     | Recursion                                                  | Iteration                             |
| ----------- | ---------------------------------------------------------- | ------------------------------------- |
| Core idea   | A function calls itself                                    | A loop repeats a block of code        |
| Code style  | Often shorter & closer to mathematical definition          | Sometimes longer but explicit         |
| Overhead    | Extra cost of function calls & stack frames                | Minimal – uses loop control variables |
| Memory use  | Risk of **stack overflow** with deep calls                 | Constant (loop variables only)        |
| Readability | Elegant for self‑similar tasks (trees, divide‑and‑conquer) | Clear for linear tasks                |

> **Choosing technique:** Use recursion when it mirrors the natural structure of the problem or when navigating hierarchical data (e.g., file systems, trees). Prefer iteration when performance and memory are critical and the problem has a simple repetitive pattern.

---

## 3  Classic Recursive Problems & Code Snippets

### 3.1 Factorial (n!)

* **Definition:** `n! = n × (n‑1)!`, with `0! = 1`.
* **Recursive C++:**

```cpp
long long factorial(int n) {
    if (n <= 1) return 1;          // base case
    return n * factorial(n - 1);   // recursive step
}
```

### 3.2 Fibonacci Sequence (nth term)

* **Definition:** `F(0)=0, F(1)=1, F(n)=F(n‑1)+F(n‑2)`.
* **Recursive C++:**

```cpp
long long fib(int n) {
    if (n <= 1) return n;               // base cases
    return fib(n-1) + fib(n-2);         // two recursive calls
}
```

> 🔎 **Note:** Plain recursive Fibonacci is exponential (O(φⁿ)). Use memoization or iteration for efficiency.

### 3.3 Tower of Hanoi

Moves a stack of disks between pegs following size rules. Recursion naturally models “move n‑1 disks to spare peg, move largest disk, move n‑1 disks onto largest”.

### 3.4 Binary Search (recursive form)

Divides a **sorted** array, discarding half each call – classic divide‑and‑conquer.

### 3.5 Recursive Sorting Algorithms

* **Merge Sort** – splits array, recursively sorts halves, merges (always O(n log n), stable).
* **Quick Sort** – partitions around pivot, recursively sorts partitions (average O(n log n), in‑place).

---

## 4  Why Use Recursion?

1. **Readability & expressiveness** – code reflects mathematical definition (factorial, Fibonacci).
2. **Natural fit for hierarchical data** – traversing trees/graphs, parsing nested structures.
3. **Divide‑and‑conquer power** – algorithms like merge sort, quicksort, binary search rely on splitting the problem.

---

## 5  Drawbacks & Risks

| Issue                  | Explanation                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------ |
| Performance overhead   | Each call pushes a new frame on the call stack (parameter passing, return address).                    |
| Stack overflow         | Deep or infinite recursion can exhaust stack memory and crash the program.                             |
| Potential inefficiency | Some recursive solutions (e.g., naïve Fibonacci) redo work; iterative or memoized versions are faster. |
| Learning curve         | Beginners may find tracing recursive flow challenging; debugging is harder than linear loops.          |

### Mitigation Tips

* Ensure a clear, reachable **base case**.
* Limit recursion depth or convert to iteration if depth is large.
* Use **tail recursion** where supported by compiler optimizations.
* Apply **memoization**/dynamic programming to avoid repeated work.

---

## 6  Best Practices for Writing Recursive Functions

1. Define the simplest input (base case) first.
2. Make progress toward the base case with each call.
3. Avoid unnecessary repeated computations (cache results if needed).
4. Consider stack size limits – for deep problems, prefer iterative or explicit stack solutions.
5. Document the recurrence relation – helps others follow the logic.

---

## 7  Key Takeaways

* Recursion breaks a problem into smaller replicas of itself until a trivial case is reached.
* Choose between recursion and iteration based on readability, performance, and memory.
* Classic recursive examples: factorial, Fibonacci, Tower of Hanoi, divide‑and‑conquer sorts, binary search.
* Drawbacks include call‑stack overhead and risk of stack overflow; iterative methods can be more efficient.

---

### Further Reading

* **“Thinking in C++, Vol 1” – Bruce Eckel**
* **“Data Structures & Algorithm Analysis in C++” – Mark Allen Weiss**
* **“Object‑Oriented Programming in C++” – Robert Lafore**