# Week 2: Organising Class Hierarchies – Packages & Namespaces (Detailed Notes)

*(Based on **COS212LL\_Y2\_02\_02 – Organising Class Hierarchies** slide deck)*

## 🎯 Learning Objectives

* Identify **packages (Java)** and **namespaces (C++)** as organisational units.
* Explain benefits: readability, maintainability, encapsulation, conflict‑avoidance.
* Create and use **packages** in Java; **namespaces** in C++.
* Manage dependencies between packages/namespaces (versioning, injection, layered architecture).

---

## 1  Why Organise Code into Hierarchies?

* Large codebases become unmanageable without clear structure.
* Grouping related classes simplifies **navigation**, prevents **name clashes**, and fosters **reuse**.
* Packages/namespaces act like *filing cabinets*—each drawer (package) holds logically related files.

---

## 2  Packages in Java

### 2.1 Definition

A **package** is a namespace that organises classes, interfaces, enums, and sub‑packages.

### 2.2 Creating a Package

```java
package myapp.utilities;
public class MyUtil { /* … */ }
```

File path mirrors package: `myapp/utilities/MyUtil.java`.

### 2.3 Access Rules Inside a Package

* Classes in the **same package** have *package‑private* access to each other (no modifier needed).
* Reduces need for `public`/`protected` when sharing helpers internally.

### 2.4 Importing

```java
import myapp.utilities.MyUtil;   // single class
import java.util.*;              // wildcard (all types)
```

> **Tip:** Avoid `.*` in production to prevent ambiguous names; import what you use.

### 2.5 Categories

| Category           | Example                  | Purpose                |
| ------------------ | ------------------------ | ---------------------- |
| **Built‑in (JDK)** | `java.lang`, `java.util` | Standard library APIs  |
| **User‑defined**   | `com.company.billing`    | Domain‑specific groups |

---

## 3  Namespaces in C++

### 3.1 Definition

A **namespace** provides a declarative region that groups identifiers (types, variables, functions) to prevent collisions, especially across libraries.

### 3.2 Creating a Namespace

```cpp
namespace math {
    double pi() { return 3.14159; }
}
```

Call with `math::pi();`.

### 3.3 Access Mechanisms

| Technique             | Syntax Example         | Pros               | Cons                |
| --------------------- | ---------------------- | ------------------ | ------------------- |
| **Scope‑resolution**  | `std::cout`            | Explicit, safest   | Verbose             |
| **using directive**   | `using namespace std;` | Short              | Risky name clashes  |
| **using declaration** | `using std::cout;`     | Import single name | Manage per‑function |

> **Best Practice:** Prefer *using declaration* inside functions, not headers, to limit scope.

---

## 4  Managing Dependencies & Architecture

### 4.1 Dependency Management Tools

* **Maven/Gradle** (Java), **npm** (JS), **NuGet** (.NET) – automate downloads, versioning.

### 4.2 Semantic Versioning

`MAJOR.MINOR.PATCH` – increment MAJOR for breaking changes, etc.

### 4.3 Layered Architecture

| Layer            | Responsibility         |
| ---------------- | ---------------------- |
| **Presentation** | UI code, controllers   |
| **Business**     | Domain logic, services |
| **Data Access**  | Repositories, DAOs     |

Enforces **separation of concerns** and minimises cross‑layer dependencies.

### 4.4 Dependency Injection (DI)

* Pass dependencies via constructors or setters instead of creating them internally.
* Improves testability (mock implementations) and decouples layers.

---

## 5  Benefits Recap

* **Organisation:** Easier to locate & navigate code.
* **Name Conflict Avoidance:** Same class name can exist in different packages/namespaces.
* **Reusability:** Components packaged for other projects.
* **Encapsulation:** Hide implementation details; expose public API.

---

## 6  Quick Quiz (with Answers)

1. **Which Java access modifier change occurs within a package?**  → Classes gain *default/package‑private* access to each other.
2. **Safest way to import a single C++ symbol?**  → `using std::cout;` inside a function.
3. **Tool to manage Java deps & versioning?**  → **Maven** (or Gradle).

---

## 7  Further Reading

* *Thinking in C++* – Bruce Eckel (namespaces chapter)
* *Effective Java* – Bloch (item on packages & access control)
* *Clean Architecture* – Bob Martin (layered design)

