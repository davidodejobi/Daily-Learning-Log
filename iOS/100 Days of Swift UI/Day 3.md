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

---

# Swift Sets Basics

## 🔹 What is a Set?

* A **set** is a collection of **unique** items.
* Sets do **not preserve order** and **do not allow duplicates**.
* Sets are optimized for **fast membership checks** (e.g., `contains`).

## 🛠 Creating Sets

### From an array-like list:

```swift
let people = Set(["Denzel Washington", "Tom Cruise", "Nicolas Cage", "Samuel L Jackson"])
```

* Duplicate values are automatically removed.
* The order is not preserved.

### Empty set with explicit type:

```swift
var people = Set<String>()
people.insert("Denzel Washington")
people.insert("Tom Cruise")
people.insert("Nicolas Cage")
people.insert("Samuel L Jackson")
```

* Use `.insert()` instead of `.append()` because sets don’t have a specific order.

## ⚡ Why Use Sets Over Arrays?

### ✅ No Duplicates

* Perfect when you **require uniqueness**, e.g., usernames, member IDs, etc.

### ✅ Performance

* `contains()` in arrays: **O(n)** – checks each item one by one.
* `contains()` in sets: **O(1)** – checks instantly using a hash.

```swift
let moviesArray = ["Inception", "Titanic", "Avatar", "The Dark Knight"]
print(moviesArray.contains("The Dark Knight")) // Slower in large arrays

let moviesSet: Set = ["Inception", "Titanic", "Avatar", "The Dark Knight"]
print(moviesSet.contains("The Dark Knight")) // Fast even with millions of items
```

## 🔍 Useful Set Methods

* `contains(item)` – Check for existence
* `count` – Total items in the set
* `sorted()` – Returns a sorted array

```swift
print(people.contains("Tom Cruise"))
print(people.count)
print(people.sorted()) // Returns ["Denzel Washington", ...] in alphabetical order
```

## 🧾 Summary

* Sets store **unique**, unordered values.
* Use `Set<Type>()` to declare an empty set.
* Use `.insert()` to add new items.
* Use sets when:

  * You need to **ensure no duplicates**.
  * You need to **check existence quickly**.
  * You don’t care about item **order**.
* Common methods: `contains()`, `count`, `sorted()`

Sets aren’t always the right choice, but for the right tasks, they outperform arrays significantly.

---

# Swift Enums Basics

## 📘 What is an Enum?

* An **enum** (short for enumeration) defines a group of related values.
* You use it when a variable should only accept a **predefined set of values**.
* Enums make your code **safer, more efficient, and easier to manage** than using raw strings or numbers.

## ⚠️ Problem With Using Strings

```swift
var selected = "Monday"
selected = "Tuesday"
selected = "January"  // ❌ Invalid but compiles
selected = "Friday "   // ❌ Has a space; not equal to "Friday"
```

Using strings can lead to typos, incorrect values, and inefficiency.

## ✅ Defining an Enum

```swift
enum Weekday {
    case monday
    case tuesday
    case wednesday
    case thursday
    case friday
}
```

* Now only these five values are allowed.

## 🔁 Using Enums

```swift
var day = Weekday.monday
day = Weekday.tuesday
```

* Swift provides **autocomplete** and prevents invalid values.

## 📝 Simplified Enum Syntax

### Multiple cases on one line:

```swift
enum Weekday {
    case monday, tuesday, wednesday, thursday, friday
}
```

### Omit enum name after first assignment:

```swift
var day = Weekday.monday

// These are automatically inferred as Weekday values
day = .tuesday
day = .friday
```

## ⚡ Performance Benefits

* Swift stores enums efficiently, often as simple integers under the hood.
* Example: `Weekday.monday` might be stored as `0`, `tuesday` as `1`, etc.

## ✅ Summary

* Use enums to define a **fixed list of related values**.
* Prevents bugs caused by invalid or misspelled strings.
* Syntax is clean, especially with dot notation and grouped cases.
* Swift stores them efficiently, making them faster and more memory-friendly.

Enums are perfect when you need a variable that must be limited to a small, specific group of values.
