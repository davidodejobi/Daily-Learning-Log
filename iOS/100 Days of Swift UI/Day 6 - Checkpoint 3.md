# Swift Coding Challenge: FizzBuzz

## 🧠 Problem Statement

Loop from 1 through 100 and for each number:

* If it’s a multiple of **3**, print `Fizz`
* If it’s a multiple of **5**, print `Buzz`
* If it’s a multiple of **3 and 5**, print `FizzBuzz`
* Otherwise, print the number itself

## ✅ Expected Output Samples

```text
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
...
100 => Buzz
```

## 💡 Hints

* Use `isMultiple(of:)` to check for divisibility.
* The condition for 3 and 5 must come **before** the individual checks.
* Use a `for` loop with a range: `1...100`

## 🧪 Try It Yourself!

<details><summary>Show Answer</summary>

```swift
for number in 1...100 {
    if number.isMultiple(of: 3) && number.isMultiple(of: 5) {
        print("FizzBuzz")
    } else if number.isMultiple(of: 3) {
        print("Fizz")
    } else if number.isMultiple(of: 5) {
        print("Buzz")
    } else {
        print(number)
    }
}
```

</details>

## 🔁 Summary

FizzBuzz is a great test of your understanding of:

* Loops
* Conditions
* Order of operations
* Divisibility

Once you’ve written and tested your code, try tweaking it:

* Can you make it more concise?
* Can you adapt it to work for other number ranges or keywords?
