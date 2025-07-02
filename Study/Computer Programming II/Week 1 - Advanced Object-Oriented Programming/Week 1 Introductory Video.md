# Week 1: Core Principles of OOP in C++ – Polymorphism, Abstract Classes & Interfaces

*(Derived from the Week 1 introductory video transcript)*

## 🎯 Learning Objectives

* Define **polymorphism** and distinguish its compile‑time vs run‑time forms.
* Explain the roles of **abstract classes** and **interfaces** in C++ design.
* Recognise how polymorphism enables robust and flexible software.

---

## 1  Opening Analogy – Yearbook Picture Day

The lecturer likens *polymorphism* to students posing differently in front of the **same backdrop** during picture day. All respond to the same "Take a photo" event, yet each expresses unique identity—mirroring how objects share an interface but perform diverse actions.

---

## 2  What Is Polymorphism?

> **Polymorphism** ("many forms") is an OOP pattern where multiple classes provide **different implementations** while sharing a **common interface** (base‑class function signatures).

### 2.1 Static (Compile‑Time) Polymorphism

* Resolved during compilation.
* Achieved via **function/method overloading** or **operator overloading** in C++.
* Example: Same function name `area()` with different parameter lists for circle vs rectangle.

### 2.2 Dynamic (Run‑Time) Polymorphism

* Resolved while the program is running.
* Achieved via **method overriding** in inheritance hierarchies, using **virtual functions**.
* Selecting the correct method relies on the object’s *actual* (derived) type, not the pointer/reference type.

---

## 3  Code Illustration – Animal Hierarchy

```cpp
#include <iostream>
using std::cout; using std::endl;

class Animal {
public:
    virtual void makeSound() const { cout << "Unknown" << endl; }
    virtual ~Animal() = default;
};

class Lion : public Animal {
public: void makeSound() const override { cout << "Roar!" << endl; } };
class Bird : public Animal {
public: void makeSound() const override { cout << "Chirp!" << endl; } };
class Snake : public Animal {
public: void makeSound() const override { cout << "Hiss!" << endl; } };

int main() {
    Animal* zoo[] { new Lion, new Bird, new Snake };
    for (Animal* a : zoo) a->makeSound();   // dynamic dispatch
    for (Animal* a : zoo) delete a;
}
```

**Key Takeaways**

* `virtual` enables run‑time dispatch.
* Base pointer interacts with multiple derived behaviours → polymorphism.
* Ensures extensibility (add `Elephant` without editing existing code).

---

## 4  Abstract Classes & Interfaces (Preview)

While the video teaser focuses on polymorphism, it hints at upcoming **abstract classes** and **interfaces**:

* **Abstract class** – cannot be instantiated; contains at least one *pure virtual* function (`=0`). Acts as a blueprint.
* **Interface** (in C++ parlance, a class with *only* pure virtual functions) – defines contract without implementation, enabling multiple inheritance of behaviour contracts.

These constructs underpin polymorphism by guaranteeing a common function set across diverse derived classes.

---

## 5  Practical Benefits

1. **Flexibility** – swap or extend behaviours without altering callers.
2. **Robustness** – code targets abstractions, reducing coupling.
3. **Maintainability** – new features added via new subclasses, not giant switch‑cases.

