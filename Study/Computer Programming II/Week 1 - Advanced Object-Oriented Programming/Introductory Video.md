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
	
		- Cannot be instantiated directly.
		- Enforces a common interface for all subclasses.

	- Interface (in C++ terms):
		-A class made up only of pure virtual functions—serves purely as a contract.

#### 4. Example: Polymorphic Animal Sounds

```cpp
class Animal {
public:
  virtual void makeSound() const { std::cout << "Some sound"; }
  virtual ~Animal() = default;
};

class Lion : public Animal {
public:
  void makeSound() const override { std::cout << "Roar"; }
};

class Bird : public Animal {
public:
  void makeSound() const override { std::cout << "Tweet"; }
};

int main() {
  std::vector<std::unique_ptr<Animal>> zoo;
  zoo.push_back(std::make_unique<Lion>());
  zoo.push_back(std::make_unique<Bird>());
  
  for (const auto& animal : zoo) {
    animal->makeSound();  // calls Lion::makeSound or Bird::makeSound
    std::cout << '\n';
  }
}
```

*   **Key Point**: `Animal*` pointer calls the correct `makeSound()` at runtime.

#### 5. Benefits of Polymorphism

*   **Flexibility**: Write code against general interfaces, extend with new types without modifying existing code.
*   **Maintainability**: Centralized interface definitions make large codebases easier to evolve.
*   **Reusability**: Common code can operate on any class implementing the interface.