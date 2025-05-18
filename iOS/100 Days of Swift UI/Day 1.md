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
```swift
print("Hello from the browser!")
```

### 🐧 3. Swift on Linux / WSL (Advanced)
```bash
# Ubuntu example setup:
sudo apt update
sudo apt install curl clang libicu-dev
curl -O https://download.swift.org/swift-5.10-release/ubuntu22.04/swift-5.10-RELEASE-ubuntu22.04.tar.gz
tar -xzf swift-5.10-RELEASE-ubuntu22.04.tar.gz
export PATH="$PWD/swift-5.10-RELEASE-ubuntu22.04/usr/bin:$PATH"
swift --version
```
Run code with:
```bash
swift Hello.swift
swiftc Hello.swift && ./Hello
```
- Use with VS Code (with Swift plugin) or terminal editors like `vim`, `nano`.

> 💡 **Windows users**: Use **WSL2 + Ubuntu**, or try **GitHub Codespaces** with a Swift container.

## ✅ Checklist
- [ ] Code runs and prints the correct output.
- [ ] You've edited and tested code variations.
- [ ] You have a playground or online setup ready to continue learning.

🧠 **Best Practice:** Reading is not enough—**run the code, break it, and learn by doing**!
