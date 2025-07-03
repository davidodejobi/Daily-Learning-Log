# Week 1: Polymorphism, Abstract Classes & Interfaces – Expanded Study Note

## 1  What Is Polymorphism?

* **Definition:** Ability of different classes to respond to the **same interface** or method call in their own way.
* **Analogy:** Yearbook photo — same backdrop (interface), but each student (class) strikes a unique pose (implementation).

---

## 2  Types of Polymorphism

### 2.1 Compile‑time (Static) Polymorphism

* **When:** Resolved by the compiler before running.
* **How:**

  * **Function Overloading:** Same function name, different parameters.
  * **Operator Overloading:** Define or redefine operators for class types.

### 2.2 Run‑time (Dynamic) Polymorphism

* **When:** Resolved as the program runs.
* **How:**

  * **Inheritance:** Derived classes inherit base interface.
  * **Virtual Functions:** `virtual` keyword in base, overridden in derived.
  * **Pointers/References to Base:** Used to call derived implementations.

### 2.3 Abstract Classes & Interfaces

* **Abstract Class** – Contains at least one pure virtual function and **cannot be instantiated**.

```cpp
class Shape {
public:
    virtual double area() const = 0;  // pure virtual – no implementation
    virtual ~Shape() = default;
};
```

* **Interface** (C++ parlance) – A class made up **only** of pure virtual functions (a contract with no data).

---

## 3  Example: Polymorphic Animal Sounds (C++ & Python)

### 3.1 C++ Version (fully commented)

```cpp
#include <iostream>
#include <memory>
#include <vector>
using std::cout; using std::endl;

// -------- Base Class --------
// Declares virtual function; enables run‑time dispatch via v‑table.
class Animal {
public:
    virtual void makeSound() const {          // default behaviour
        cout << "Some sound";
    }
    virtual ~Animal() = default;              // virtual destructor (good practice)
};

// -------- Derived Classes --------
class Lion : public Animal {
public:
    void makeSound() const override {         // override ensures signature match
        cout << "Roar";
    }
};

class Bird : public Animal {
public:
    void makeSound() const override {
        cout << "Tweet";
    }
};

int main() {
    // Store heterogeneous objects via smart pointers to the base class.
    std::vector<std::unique_ptr<Animal>> zoo;
    zoo.push_back(std::make_unique<Lion>());
    zoo.push_back(std::make_unique<Bird>());

    // Same call invokes different implementations at run time.
    for (const auto &animal : zoo) {
        animal->makeSound();
        cout << '\n';
    }
}
```

### 3.2 Python Equivalent (Duck Typing)

```python
class Animal:
    def make_sound(self):
        print("Some sound")

class Lion(Animal):
    def make_sound(self):
        print("Roar")

class Bird(Animal):
    def make_sound(self):
        print("Tweet")

zoo = [Lion(), Bird()]
for animal in zoo:
    animal.make_sound()   # dynamic dispatch via duck typing
```

**Key parallels:** In C++ we declare `virtual`/`override`; Python relies on dynamic method lookup without extra keywords.

---

## 4  Benefits of Polymorphism

* **Flexibility:** Write code against general interfaces; extend with new types without modifying existing code.
* **Maintainability:** Centralised interface definitions make large codebases easier to evolve.
* **Reusability:** Common code can operate on any class implementing the interface.
