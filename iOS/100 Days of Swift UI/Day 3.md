# Swift Arrays Basics

## 📦 What is an Array?

* An **array** is a data type that can hold multiple values in a single variable.
* Arrays store data **in order** and can contain any number of items.

```swift
var beatles = ["John", "Paul", "George", "Ringo"]
let numbers = [4, 8, 15, 16, 23, 42]
var temperatures = [25.3, 28.2, 26.4]
```

## 📥 Reading from Arrays

* Arrays use **zero-based indexing**:

```swift
print(beatles[0]) // John
print(numbers[1]) // 8
print(temperatures[2]) // 26.4
```

* Accessing an invalid index will crash your program.

## ➕ Adding Items

Use `.append()` to add a new item:

```swift
beatles.append("Adrian")
beatles.append("Vivian")
```

## ⚠️ Type Safety

* Arrays can only contain **one data type**.

```swift
temperatures.append("Chris") // ❌ Error: can't add String to [Double]
```

```swift
let firstBeatle = beatles[0]      // String
let firstNumber = numbers[0]      // Int
let notAllowed = firstBeatle + firstNumber // ❌ Error
```

## 🛠 Creating Empty Arrays with Type

```swift
var scores = Array<Int>()
scores.append(100)
scores.append(80)
```

Alternative shorthand syntax:

```swift
var albums = [String]()
albums.append("Folklore")
```

If you provide initial values, Swift will infer the type:

```swift
var albums = ["Folklore"]
albums.append("Red")
```

## 🧰 Useful Array Methods

### 1. Count Items

```swift
print(albums.count)
```

### 2. Remove Items

```swift
var characters = ["Lana", "Pam", "Ray", "Sterling"]
characters.remove(at: 2)
characters.removeAll()
```

### 3. Check for an Item

```swift
let bondMovies = ["Casino Royale", "Spectre", "No Time To Die"]
print(bondMovies.contains("Frozen")) // false
```

### 4. Sort the Array

```swift
let cities = ["London", "Tokyo", "Rome", "Budapest"]
print(cities.sorted())
```

### 5. Reverse the Array

```swift
let presidents = ["Bush", "Obama", "Trump", "Biden"]
let reversedPresidents = presidents.reversed()
print(reversedPresidents)
```

* `.reversed()` returns a **ReversedCollection**, not a plain array.

## 🔁 Bonus: Works with Strings Too!

```swift
let word = "swift"
let sortedLetters = word.sorted() // ["f", "i", "s", "t", "w"]
```

## ✅ Summary

* Arrays store multiple values of the same type.
* Use brackets `[]` to create arrays.
* Read with `array[index]`, add with `.append()`.
* Use `.count`, `.remove()`, `.contains()`, `.sorted()`, `.reversed()` for powerful array manipulation.


---

# Swift Dictionaries Basics

## 📘 What is a Dictionary?

* A **dictionary** stores multiple values by assigning them to **unique keys**.
* Unlike arrays, dictionaries do not store values in order.
* Each key maps to exactly one value.

```swift
let employee = [
    "name": "Taylor Swift",
    "job": "Singer",
    "location": "Nashville"
]
```

## 🔍 Reading from a Dictionary

* Access values using keys:

```swift
print(employee["name"])
print(employee["job"])
print(employee["location"])
```

* Output may include `Optional(...)` because Swift doesn’t know for sure if the key exists.

### ✅ Safe Access with Default Value

```swift
print(employee["name", default: "Unknown"])
print(employee["manager", default: "Not assigned"])
```

## ⚠️ Optionals

* Accessing a missing key returns `nil`, which is wrapped as an **optional**.
* Optionals represent the possibility of no value.
* Use default values to avoid crashes.

## 🔁 Dictionaries with Other Types

### Example 1: Dictionary with Bool Values

```swift
let hasGraduated = [
    "Eric": false,
    "Maeve": true,
    "Otis": false
]
```

### Example 2: Int Keys

```swift
let olympics = [
    2012: "London",
    2016: "Rio de Janeiro",
    2021: "Tokyo"
]

print(olympics[2012, default: "Unknown"])
```

## 🛠 Creating Empty Dictionaries

### Syntax 1: Full type declaration

```swift
var heights = [String: Int]()
heights["Yao Ming"] = 229
heights["Shaquille O'Neal"] = 216
```

### Syntax 2: Shorthand

```swift
var archEnemies = [String: String]()
archEnemies["Batman"] = "The Joker"
archEnemies["Superman"] = "Lex Luthor"
```

### Overwriting Values

```swift
archEnemies["Batman"] = "Penguin" // Replaces "The Joker"
```

## 📏 Dictionary Methods

* `.count` returns the number of key-value pairs.
* `.removeAll()` clears all entries.

```swift
print(archEnemies.count)
archEnemies.removeAll()
```

## ✅ Summary

* Dictionaries store key-value pairs with unique keys.
* Use keys to access values; missing keys return optionals.
* Provide default values to safely handle missing keys.
* You can store different types in dictionaries (e.g., Int, Bool).
* Useful methods: \`.count
