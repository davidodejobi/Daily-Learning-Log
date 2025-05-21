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
