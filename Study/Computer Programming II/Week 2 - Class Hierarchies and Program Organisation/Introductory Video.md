
*   Introduction to **Constructors and Destructors**
*   Types of constructors
*   Constructor overloading
*   Destructors and their role
*   Constructor initializer lists
*   Static members in classes
*   Copy constructor and shallow vs deep copy

# 🧱 **Constructors**

### ✅ What is a Constructor?

*   A special method called **automatically** when an object is created.
*   Its **name matches the class name** and **has no return type**.

### ✅ Types of Constructors

| Type                                  | Description                                               |
| ------------------------------------- | --------------------------------------------------------- |
| **Default Constructor**               | Takes no parameters or all parameters have default values |
| **Parameterized Constructor**         | Takes parameters to initialize data members               |
| **Copy Constructor**                  | Creates a new object as a copy of an existing one         |
| **Constructor with Initializer List** | Initializes members before the constructor body runs      |
|                                       |                                                           |

```cpp
class Person {
  int age;
public:
  Person(int a) : age(a) { } // initializer list
};
```

## 🔁 **Constructor Overloading**

*   Multiple constructors in the same class with different parameter lists.

```cpp
class Box {
public:
  Box() { }              // Default
  Box(int l) { }         // Parameterized
  Box(int l, int w) { }  // Another overload
};
```

## ❌ **Destructors**

*   Special function that **cleans up resources** when an object goes out of scope or is deleted.
*   Declared using `~ClassName()` and takes **no parameters**.
*   Only **one destructor** allowed per class.

```cpp
class Demo {
public:
  ~Demo() {
    std::cout << "Destructor called" << std::endl;
  }
};
```

## 📌 **Copy Constructor**

*   Syntax: `ClassName(const ClassName &other)`
*   Called:
    *   When a new object is created from an existing one
    *   Passed by value
    *   Returned by value

```
class Student {
  int id;
public:
  Student(int x) { id = x; }
  Student(const Student &s) { id = s.id; }
};

```

## ⚠️ Shallow Copy vs Deep Copy

| Concept          | Description                                                      |
| ---------------- | ---------------------------------------------------------------- |
| **Shallow Copy** | Copies pointer value → multiple objects point to the same memory |
| **Deep Copy**    | Duplicates the actual memory content                             |

Use deep copy to avoid **shared memory issues** when dealing with **dynamic allocation**.

## ⚙️ **Static Members**

*   **Static data members** are shared among **all instances** of the class.
*   **Static member functions** can be called without creating an object.

```cpp
class Counter {
public:
  static int count;
  static void increment() { count++; }
};
int Counter::count = 0;
```

## 🧠 Summary

*   Constructors initialize, destructors clean up
*   Constructor overloading allows flexibility
*   Use initializer lists for efficient member setup
*   Copy constructors are critical for managing object copying
*   Static members belong to the class, not the object
