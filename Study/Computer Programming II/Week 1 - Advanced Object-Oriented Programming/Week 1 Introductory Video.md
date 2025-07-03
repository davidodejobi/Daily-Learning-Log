## 1. What Is Polymorphism?

- Definition: Ability of different classes to respond to the same interface or method call in their own way.
- Analogy: Yearbook photo — same backdrop (interface), but each student (class) strikes a unique pose (implementation).

## 2. Types of Polymorphism

#### 1. Compile-time (Static) Polymorphism
	- When: Resolved by the compiler before running.
	- How:
		- Function Overloading: Same function name, different parameters.
		- Operator Overloading: Define or redefine operators for class types.

#### 2.  Run-time (Dynamic) Polymorphism
	- When: Resolved as the program runs.
	- How:
		- Inheritance: Derived classes inherit base interface.
		- Virtual Functions: virtual keyword in base, overridden in derived.
		- Pointers/References to Base: Used to call derived implementations.

#### 3. Abstract Classes & Interfaces
- Abstract Class:
	- Contains at least one pure virtual function:
```cpp
class Shape {
public:
  virtual double area() const = 0;  // no implementation
};

```