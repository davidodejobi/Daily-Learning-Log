
## 📚 Week 3: Implementing Iterators, Enumerators, Lists, Stacks, and Queues
* * *
## 🧠 **Big Idea**
Just like organizing a library improves book retrieval, organizing variables using **data structures** improves efficiency in complex programs.
* * *

## 🧾 **Why Use Data Structures?**
*   Helps manage large sets of data
*   Organizes memory efficiently
*   Reduces complexity when accessing, modifying, or removing data
*   Ensures structured code and easier maintenance

## 🔁 **1\. Iterators (a.k.a. "itr")**

### ✅ Definition:

Objects that allow you to traverse containers (like vectors, lists) element by element.
### 📌 Uses:
*   Accessing, modifying, or removing elements in a sequence
*   Works like a cursor to step through collections
### 🔍 Example (C++):

```cpp
std::vector<int> numbers = {1, 2, 3};
for (auto it = numbers.begin(); it != numbers.end(); ++it) {
    std::cout << *it << " ";
}
```

🔢 **2\. Enumerators (Enums)**
------------------------------

### ✅ Definition:

User-defined types with a collection of named integer constants.

### 📌 Features:

*   Improve code **readability** by using names instead of numbers
*   Prevent assigning invalid values to variables
*   Help define fixed categories (e.g., days of the week)

### 🔍 Example:

```cpp
enum Day { Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday };
Day today = Wednesday;
```

### 🎯 When to Use:

*   To replace **"magic numbers"** with meaningful names
*   When a variable should only take on **a specific set of values**

* * *

📋 **3\. Lists**
----------------

(Covered further in later part of Week 3 material)

Used for flexible-sized collections of elements, especially when insertions/deletions are frequent.

* * *

📦 Summary So Far
-----------------

| Structure | Purpose | C++ Feature |
| --- | --- | --- |
| Iterator | Traverse containers | `std::iterator` |
| Enumerator | Define symbolic constants | `enum` |
| List | Store ordered collection of elements | `std::list` |

* * *

Would you like me to continue with the rest of Week 3's structures (Stacks and Queues) based on the remaining transcript?

## Response:
Here’s a **detailed explanation and expansion** of your **Week 3 COS202 summary** on _"Implementing Iterators, Enumerators, Lists, Stacks, and Queues"_, structured as full lecture notes to help you understand and revise effectively:

* * *

🧠 Week 3: Implementing Iterators, Enumerators, Lists, Stacks, and Queues
=========================================================================

**Course:** Computer Programming II (COS 202)  
**Theme:** Choosing and implementing the right data structure for effective program design.

* * *

🔶 1. What Are Data Structures?
-------------------------------

**Definition**:  
A data structure is a specialized way of organizing and storing data in a computer so that it can be accessed and modified efficiently.

**Why They Matter**:

*   Control **data flow**
*   Make searching and updating faster
*   Organize complexity for easier maintenance

* * *

🔁 2. Iterators in C++
----------------------

### 🔷 What is an Iterator?

An **iterator** is an object used to point to elements in a container (like a vector, list, set, etc.) and traverse the elements sequentially.

### 🔧 How It Works:

*   Similar to a pointer
*   Can increment, dereference, and compare
*   Used with STL containers (`vector`, `list`, `map`, etc.)

### 🔍 Example:

```cpp
std::vector<int> numbers = {1, 2, 3};
for (std::vector<int>::iterator it = numbers.begin(); it != numbers.end(); ++it) {
    std::cout << *it << " ";
}
```

### ✅ Benefits:

*   Simplifies traversal
*   Makes code cleaner and more readable
*   Abstracts internal data representation

* * *

🔢 3. Enumerators (Enums)
-------------------------

### 🔷 What is an Enumerator?

An **enumerator** (or `enum`) is a user-defined type that consists of named integral constants.

### 📌 Purpose:

*   Improves **code readability** by replacing numeric constants with names
*   Prevents invalid values from being assigned to variables

### 🔍 Example:

```cpp
enum Day { Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday };
Day today = Wednesday;
```

### ✅ Benefits:

*   Prevents use of “magic numbers”
*   Ensures values stay within a **valid set**
*   Helps enforce strict type safety

* * *

📋 4. Lists
-----------

### 🔷 What is a List?

A **list** is a linear data structure that holds items in a sequence. It can be implemented in two major ways:

1.  **Arrays**
2.  **Linked Lists**

* * *

### 📌 Arrays

*   **Fixed size**
*   **Contiguous memory**
*   **Fast random access** (`O(1)`)
*   Poor for insertions/deletions in the middle (`O(n)`)

```cpp
int arr[5] = {1, 2, 3, 4, 5};
```

* * *

### 📌 Linked Lists

*   **Dynamic size**
*   Nodes are **connected using pointers**
*   **Efficient insertion/deletion** (`O(1)` if position known)
*   Slower random access (`O(n)`)

```cpp
struct Node {
  int data;
  Node* next;
};
```

* * *

🥞 5. Stacks
------------

### 🔷 What is a Stack?

A **Last-In-First-Out (LIFO)** data structure.

### 📌 Operations:

*   `push(item)` – add to top
*   `pop()` – remove top item
*   `peek()` – look at top item without removing

### 🔍 Example Use Case:

*   Undo functionality in text editors
*   Parsing expressions

```cpp
std::stack<int> s;
s.push(10);
s.pop();
```

* * *

📥 6. Queues
------------

### 🔷 What is a Queue?

A **First-In-First-Out (FIFO)** data structure.

### 📌 Operations:

*   `enqueue(item)` – add to rear
*   `dequeue()` – remove from front
*   `peek()` – get front item

### 🔍 Example Use Case:

*   Print queue
*   Task scheduling

```cpp
std::queue<int> q;
q.push(5);
q.pop();
```

* * *

🧠 Key Comparisons
------------------

| Feature | Array | Linked List | Stack | Queue |
| --- | --- | --- | --- | --- |
| Size | Fixed | Dynamic | Dynamic | Dynamic |
| Access Time | Fast (O(1)) | Slow (O(n)) | Top only | Front only |
| Insert/Delete | Costly | Efficient | Top only | Ends only |

* * *

🧠 Application Exercises
------------------------

1.  **Shopping Cart App**: Use a list to add/remove items, and calculate total price.
2.  **Bank Queue Simulation**: Use a queue to manage customer arrival/departure.
3.  **Music Playlist**: Use a linked list to add/remove/play songs in order.

* * *

💭 Reflection Questions
-----------------------

*   How does choosing between a stack, queue, or list affect performance?
*   When is an array better than a linked list, and vice versa?
*   How do iterators simplify looping over collections?
*   What structure fits real-world use cases like browsers, banking apps, or schedulers?

* * *

🛠️ Skills You’ve Gained
------------------------

*   Understanding of **data structure fundamentals**
*   Ability to **select the right structure** for each task
*   **C++ implementation skills**
*   Problem-solving using **algorithms**

* * *

📚 References for Deeper Study
------------------------------

*   **Thinking in C++** – Bruce Eckel
*   **Data Structures and Algorithm Analysis in C++** – Mark Allen Weiss
*   **Object-Oriented Programming in C++** – Robert Lafore