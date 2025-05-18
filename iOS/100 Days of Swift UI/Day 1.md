# Running the Book’s Code

## 🧠 Key Concepts
- All sample code in the book should be **typed and tested by you**.
- You'll use **Xcode Playgrounds** to run Swift code easily.
- Playgrounds show results live next to your code – perfect for learning.

## 🖥️ Xcode Playground Setup (macOS)
1. **Install Xcode 15+**
   - Get it from the **Mac App Store** (free).

2. **Create a Playground**
   - Open Xcode → `File ▸ New ▸ Playground…`
   - Select `Blank` under the **macOS** tab.
   - Save it somewhere easy to find (e.g. `Documents/SwiftBook.playground`)

3. **Try It Out**
```swift
var greeting = "Hello, Swift!"
print(greeting) // ⇒ Hello, Swift!
```
- The first run may take a few seconds; later ones are faster.

4. **Tips**
- Use one playground for the entire book, or a new one per chapter.
- Code changes are reflected live—experiment freely!

## 🌐 Alternatives if You Don’t Have a Mac

### 🛜 1. Swift Playgrounds (iPad)
- Free from the iPad App Store.
- Create a blank playground and follow along with the same Swift syntax.

### 🌍 2. Online Swift REPLs
- Use in any browser:
  - [SwiftFiddle](https://swiftfiddle.com)
  - [Replit](https://replit.com)
- Great for small tests and quick practice.

## ✅ Checklist
- [ ] Code runs and prints the correct output.
- [ ] You've edited and tested code variations.
- [ ] You have a playground or online setup ready to continue learning.

🧠 **Best Practice:** Reading is not enough—**run the code, break it, and learn by doing**!

# Variables and Constants in Swift

## Key Concepts
- **Variables** are used to store values that can change over time.
- **Constants** are used to store values that never change.
- Swift encourages the use of **constants (`let`)** whenever possible for safety and performance.
- Use **`print()`** to view variable values in a playground during development.
- Swift uses **camelCase** for naming variables and constants.

## Variables (`var`)
- Use `var` to declare a variable (i.e., a value that can change).

```swi
swift
var greeting = "Hello, playground"
greeting = "Hi there"
```

- You can reassign a variable without using `var` again:

swift
var name = "Ted"
name = "Rebecca"
name = "Keeley"

- Old values are **discarded** as soon as a new one is assigned.

## 🔒 Constants (`let`)
- Use `let` to declare a constant (i.e., a value that can’t change).

swift
let character = "Daphne"

- Trying to change a constant will cause a **compiler error**:

swift
\let character = "Daphne"
//character = "Eloise"   // ❌ Error: Cannot assign to value: 'character' is a 'let' constant
//*/\*character = "Francesca" // ❌ Error: Same here

- Always prefer `let` over `var` when you don’t need to change the value.

## 🖨 Printing Values
- Use `print()` to inspect the current value of a variable:

swift
var playerName = "Roy"
print(playerName)

playerName = "Dani"
print(playerName)

playerName = "Sam"
print(playerName)

- This is helpful in **Playgrounds** but not typically used in production apps.

## 🧱 Syntax Breakdown
1. `var` or `let` — keyword to declare variable or constant.
2. `name` — your identifier, can be anything but should be descriptive.
3. `=` — assignment operator.
4. `"value"` — the assigned value, enclosed in double quotes for strings.

## 💡 Tips
- Swift does **not require semicolons** at the end of lines.
- Use **camelCase** for naming: `playerName`, `dogBreed`, `meaningOfLife`.
- Always use the same name consistently; `playerName` and `playername` are different in Swift.
- The `import Cocoa` statement in macOS Playgrounds gives access to Apple’s UI frameworks (important—don’t delete it).

## 🧼 Best Practice
- Prefer `let` over `var` unless you **know** you need to change the value later. This leads to:
  - Safer code (fewer unintended changes)
  - Better performance (compiler optimization)

This gives you the foundation to store and manage data in Swift efficiently.

