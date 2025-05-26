# Week 4: Understanding Search Algorithms

## 🎯 Learning Objectives

* Understand the concept of search algorithms and their significance.
* Explore searching within collections such as arrays and lists.
* Learn how linear and binary search algorithms function.
* Apply search algorithms using practical C++.

## 🧠 Introduction

Searching is fundamental in programming when working with data. Whether you need to find an element in a list, array, or any data structure, search algorithms ensure efficiency. This week focuses on two key algorithms: **linear search** and **binary search**.

## 🔍 Linear Search

### ✅ What is Linear Search?

* A simple algorithm that checks each element sequentially until the target is found or the end is reached.
* Works on both sorted and unsorted data.
* Time complexity: O(n).

### 📌 Algorithm Steps

1. Start from the first element.
2. Compare each element with the target.
3. If a match is found, return its index.
4. If not, continue until the end.
5. If not found, return -1.

### 🔧 C++ Example

```cpp
int linearSearch(int arr[], int size, int key) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == key) return i;
    }
    return -1;
}
```

### 🔧 Python Example

```python
def linear_search(arr, key):
    for i in range(len(arr)):
        if arr[i] == key:
            return i
    return -1
```

## 📐 Binary Search

### ✅ What is Binary Search?

* A more efficient search method than linear search.
* Requires the data to be **sorted**.
* Uses a divide-and-conquer approach.
* Time complexity: O(log n).

### 📌 Algorithm Steps

1. Initialize two pointers: `Low` (start) and `High` (end).
2. While `Low <= High`:

   * Calculate `Mid = (Low + High) / 2`.
   * If `arr[Mid] == target`, return `Mid`.
   * If `arr[Mid] < target`, set `Low = Mid + 1`.
   * If `arr[Mid] > target`, set `High = Mid - 1`.
3. If not found, return -1.

### 🔧 C++ Example

```cpp
int binarySearch(int arr[], int size, int key) {
    int low = 0, high = size - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == key) return mid;
        else if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

### 🔧 Python Example

```python
def binary_search(arr, key):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == key:
            return mid
        elif arr[mid] < key:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```

## 🧭 Searching in Collections

| Collection | Linear Search | Binary Search | Notes                                      |
| ---------- | ------------- | ------------- | ------------------------------------------ |
| Arrays     | Yes           | Yes           | Fast access (O(1)); fixed size             |
| Vectors    | Yes           | Yes           | Dynamic size; STL container                |
| Lists      | Yes           | No            | Doubly linked list; no random access       |
| Maps       | No (typical)  | Yes           | Efficient associative container (O(log n)) |

## 🏎️ Performance Comparison

* **Linear Search**: Simple but inefficient for large datasets.
* **Binary Search**: Faster for large, sorted datasets.

## 🧪 Practical Example: Search in Student Names

### 🔧 C++ Example

```cpp
std::vector<std::string> names = {"Alice", "Bob", "Charlie"};
std::string target = "Charlie";
for (int i = 0; i < names.size(); i++) {
    if (names[i] == target) {
        std::cout << "Found at index " << i;
        break;
    }
}
```

### 🔧 Python Example

```python
names = ["Alice", "Bob", "Charlie"]
target = "Charlie"
for i in range(len(names)):
    if names[i] == target:
        print(f"Found at index {i}")
        break
```

## 🧠 Key Insights

* Linear search is universal but less efficient for large data.
* Binary search is efficient but only on sorted data.
* Choose the appropriate algorithm based on the data structure and problem context.

## 📚 Further Reading

* "Thinking in C++" – Bruce Eckel
* "Data Structures and Algorithm Analysis in C++" – Mark Allen Weiss
* "Object-Oriented Programming in C++" – Robert Lafore
* "Effective Java" – Joshua Bloch
* "Design Patterns" – Erich Gamma et al.
* "Clean Architecture" – Robert C. Martin
