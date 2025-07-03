
## 🧠 **Learning Objectives**

*   Understand and implement **polymorphism**
*   Create and use **interfaces**
*   Grasp the use of **abstract classes**
*   Apply **advanced OOP principles** to solve problems

## 🔁 **OOP Recap: Key Concepts**

*   **Class**: Blueprint for creating objects (defines properties + methods)
*   **Object**: Instance of a class, holds actual data
*   **Inheritance**: Derived class inherits properties/methods from a base class
*   **Encapsulation**: Hide sensitive data (via `private`), expose only what's necessary
*   **Polymorphism**: Same interface, different implementations

## 🧩 **Polymorphism in Detail**

### 📌 Definition:

*   "Many forms" – enables objects of different classes to be treated as instances of a common superclass.
*   Each object responds differently to the **same method call**.

### 🧠 Types of Polymorphism:

| Type | Description |
| --- | --- |
| **Compile-Time** | aka **Method Overloading**: same method name, different parameter lists |
| **Run-Time** | aka **Method Overriding**: subclass redefines a method from superclass |

### ✅ Why It's Important:

*   Enhances **code reusability**
*   Improves **flexibility** and **maintainability**
*   Enables **dynamic binding** (method invoked is determined at runtime)

* * *

🧱 **Abstract Classes**
-----------------------

### 📌 What is an Abstract Class?

*   A class **you can't instantiate** directly
*   Contains at least one **pure virtual function**:
    ```cpp
    class Animal {
      virtual void makeSound() = 0;  // pure virtual
    };
    ```

### 🧰 Features:

*   Can have **both** pure virtual and concrete (implemented) methods
*   Used to define a **shared interface** and base implementation for derived classes

### 💡 Use Case:

*   Representing a **generic concept** (e.g., Vehicle, Animal)
*   Sharing code across subclasses, but **forcing** them to implement specific behaviors

* * *

🔌 **Interfaces in C++**
------------------------

### 📌 What is an Interface?

*   Implemented using **pure abstract classes**
*   Contains **only pure virtual functions**
*   No data members or implemented methods

### 🧰 Features:

*   Define a **contract** for implementing classes
*   Support **multiple inheritance**
*   Promote **modular** and **flexible** code

### 🔀 Multiple Interfaces:

*   A class can implement multiple interfaces:
    ```cpp
    class Animal {
      virtual void makeSound() = 0;
    };
    class Movable {
      virtual void move() = 0;
    };
    class Dog : public Animal, public Movable {
      void makeSound() override { /* ... */ }
      void move() override { /* ... */ }
    };
    ```

* * *

🧠 **Abstract Class vs Interface**
----------------------------------

| Feature | Abstract Class | Interface (Pure Abstract Class) |
| --- | --- | --- |
| Instantiable? | ❌ | ❌ |
| Pure Virtual Methods | ✅ (at least one) | ✅ (all) |
| Concrete Methods | ✅ | ❌ |
| Member Variables | ✅ | ❌ |
| Multiple Inheritance | ✅ | ✅ |

* * *

📝 **Sample Questions**
-----------------------

1.  **Which is true about C++ interfaces?**  
    ✅ A class can implement multiple interfaces
2.  **Which is false about abstract classes?**  
    ❌ Abstract classes can be instantiated

* * *

📚 **Recommended Reading**
--------------------------

*   Lafore, R. – _Object-Oriented Programming in C++_
*   Weiss, M.A. – _Data Structures and Algorithm Analysis in C++_
*   Gamma et al. – _Design Patterns_
*   Hunt & Thomas – _The Pragmatic Programmer_
