# Week 1: Advanced OOP Foundations – Polymorphism, Abstract Classes & Interfaces (C++ + Python)

## 🧠 Learning Objectives

* Understand and implement **polymorphism** (static & dynamic)
* Create and use **interfaces** in C++ (pure abstract classes)
* Grasp the role of **abstract classes**
* Apply advanced OOP principles to craft flexible solutions

---

## 🔁 OOP Recap: Key Concepts

| Concept           | Summary                                                       |
| ----------------- | ------------------------------------------------------------- |
| **Class**         | Blueprint for creating objects (defines properties + methods) |
| **Object**        | Instance of a class, stores actual data                       |
| **Inheritance**   | Derived class reuses/extends base functionality               |
| **Encapsulation** | Hide sensitive data via `private`; expose via getters/setters |
| **Polymorphism**  | Same interface → many implementations                         |

---

## 🧩 Polymorphism in Detail

### 📌 Definition

> “Many forms” — enables objects of different classes to be treated as instances of a common superclass, each responding differently to the **same method call**.

### 🧠 Types of Polymorphism

| Type             | Description               | C++ Mechanism                      |
| ---------------- | ------------------------- | ---------------------------------- |
| **Compile‑Time** | Resolved by compiler      | Function/Operator **Overloading**  |
| **Run‑Time**     | Resolved during execution | **Virtual** functions + overriding |

### ✅ Why It Matters

* **Code reusability & flexibility**
* **Maintainability** via dynamic binding
* Extensible: new subclasses without changing caller code

---

## 🧱 Abstract Classes

| Feature       | Details                                        |
| ------------- | ---------------------------------------------- |
| Instantiation | ❌ Cannot instantiate directly                  |
| Requirement   | At least one **pure virtual** function (`=0`)  |
| Mixed Methods | May include concrete methods & data members    |
| Purpose       | Provide shared interface & base implementation |

```cpp
class Shape {
public:
    virtual double area() const = 0;   // pure virtual → no impl
    virtual ~Shape() = default;        // good practice
};
```

### 💡 Use‑Cases

* Generic concepts (Vehicle, Animal) where subclasses **must** implement certain behaviours.

---

## 🔌 Interfaces in C++

* Implemented as **pure abstract classes** (all methods `=0`, no data).
* Provide a **contract**; multiple interfaces supported via multiple inheritance.

```cpp
class Speakable {                       // interface
public:
    virtual void speak() const = 0;
};
```

### 🔀 Multiple Interfaces Example

```cpp
class Animal { public: virtual void makeSound() const = 0; };
class Movable { public: virtual void move() const = 0; };

class Dog : public Animal, public Movable {
public:
    void makeSound() const override { /*...*/ }
    void move() const override      { /*...*/ }
};
```

---

## 🧠 Abstract Class vs Interface Comparison

| Feature                   | Abstract Class | Interface |
| ------------------------- | -------------- | --------- |
| Instantiable?             | ❌              | ❌         |
| At least one pure virtual | ✅              | ✅ (all)   |
| Concrete methods allowed  | ✅              | ❌         |
| Member variables          | ✅              | ❌         |
| Multiple inheritance      | ✅              | ✅         |

---

## 📝 Code Examples (with comments)

### 1. C++ Polymorphic Animal Sounds

```cpp
#include <iostream>
#include <memory>
#include <vector>
using std::cout; using std::endl;

// ---------- Base Class ----------
class Animal {
public:
    virtual void makeSound() const {          // default fallback
        cout << "Some sound";
    }
    virtual ~Animal() = default;              // virtual dtor for safety
};

// ---------- Derived Classes ----------
class Lion : public Animal {
public:
    void makeSound() const override {         // override = checked at compile
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
    // Store different animals via base‑class smart pointers
    std::vector<std::unique_ptr<Animal>> zoo;
    zoo.push_back(std::make_unique<Lion>());
    zoo.push_back(std::make_unique<Bird>());

    // Dynamic dispatch: same call, varied behaviour
    for (const auto &a : zoo) {
        a->makeSound();
        cout << '\n';
    }
}
```

### 2. Python Equivalent

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
for a in zoo:
    a.make_sound()   # dynamic dispatch via duck typing
```

*Python uses dynamic lookup – no `virtual` keyword needed.*

---

## 🔑 Benefits Recap

* **Flexibility & Extensibility** – add new types easily.
* **Maintainability** – interface‑centric design reduces coupling.
* **Reusability** – algorithms operate on base pointers or interfaces.

---

## 📚 Recommended Reading

* Lafore – *Object‑Oriented Programming in C++*
* Weiss – *Data Structures and Algorithm Analysis in C++*
* Gamma et al. – *Design Patterns*
* Hunt & Thomas – *The Pragmatic Programmer*

---

**End of Week 1 Extended OOP Note**
