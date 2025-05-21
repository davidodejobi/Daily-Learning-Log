Your goal is to write a Swift playground that:

1. Creates a constant holding any temperature in Celsius.
2. Converts it to Fahrenheit by multiplying by 9, dividing by 5, then adding 32.
3. Prints the result for the user, showing both the Celsius and Fahrenheit values.


My solution

```swift
import Cocoa

let temperature: Double = 25.0
let fahrenheit: Double = (temperature * 9.0 / 5.0) + 32.0
print("\(temperature) degrees Celsius is equal to \(fahrenheit) degrees Fahrenheit.")
``` 
