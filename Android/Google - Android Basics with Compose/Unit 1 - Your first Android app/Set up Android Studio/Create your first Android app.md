# Compose Greeting Card

> **Source** – [Install Android Studio & Build Your First Compose App](https://developer.android.com/codelabs/basic-android-kotlin-compose-install-android-studio)
> This note distills the steps into a quick, self‑study guide. Follow along or skim for reference.

---

## 1  Before You Begin

| Requirement                                    | Detail                                                                                                                |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Android Studio**                             | Install the *latest* stable release. Verify [system requirements](https://developer.android.com/studio#Requirements). |
| **Kotlin basics**                              | Know variables, functions, and string templates.                                                                      |
| **What you’ll build**                          | A Jetpack Compose "Greeting Card" that introduces you by name.                                                        |
| **Key skills**                                 | • Create a project from **Empty Activity** template                                                                   |
| • Use **Preview** & hot‑reload                 |                                                                                                                       |
| • Edit text in a composable                    |                                                                                                                       |
| • Wrap UI in **Surface** and tint with `Color` |                                                                                                                       |
| • Add spacing via `Modifier.padding()`         |                                                                                                                       |

---

## 2  Create a New Project

1. **Launch Android Studio** → *New Project*.
2. Select **Phone & Tablet ▸ Empty Activity** → **Next**.
3. Configure:

   * **Name** → `Greeting Card`
   * **Package** → default (`com.example.greetingcard`)
   * **Minimum SDK** → `API 24 (Nougat)`
4. Click **Finish** and wait for Gradle sync.

> **Tip** – Click **Split** (top‑right) to view *Code* & *Design* panes side‑by‑side.

### Project Pane Cheatsheet

* **Android** view = logical grouping for dev work (preferred).
* **Project Source Files** view = actual directory tree.

---

## 3  Starter Code Walkthrough

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            GreetingCardTheme {
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colorScheme.background
                ) {
                    Greeting("Android")
                }
            }
        }
    }
}

@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text("Hello $name!", modifier = modifier)
}
```

* **`onCreate()`** – entry point for Android activity.
* **`setContent { … }`** – Compose runtime; calls composable functions.
* **`@Composable` functions** – capitalized names, no return value.
* **`GreetingPreview()`** (omitted here) has `@Preview` to render in Design pane.

---

## 4  Customize the Text

1. Change greeting:

   ```kotlin
   Text("Hi, my name is $name!", modifier = modifier)
   ```
2. Update preview sample:

   ```kotlin
   @Preview(showBackground = true)
   @Composable
   fun GreetingPreview() {
       GreetingCardTheme { Greeting("YourName") }
   }
   ```

   > **Live reload** – Build & Refresh if preview stalls.

---

## 5  Add Background with `Surface`

```kotlin
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Surface(color = Color.Cyan) {
        Text("Hi, my name is $name!", modifier = modifier)
    }
}
```

**Imports to add** (optimize afterward):

```kotlin
import androidx.compose.ui.graphics.Color
```

---

## 6  Add Padding via `Modifier`

```kotlin
import androidx.compose.foundation.layout.padding
import androidx.compose.ui.unit.dp

@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Surface(color = Color.Cyan) {
        Text(
            "Hi, my name is $name!",
            modifier = modifier.padding(24.dp)
        )
    }
}
```

* `Modifier` chains let you decorate UIs.
* `dp` = density‑independent pixels.

---

## 7  Full Solution

```kotlin
package com.example.greetingcard

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.padding
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import com.example.greetingcard.ui.theme.GreetingCardTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            GreetingCardTheme {
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colorScheme.background
                ) {
                    Greeting("Android")
                }
            }
        }
    }
}

@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Surface(color = Color.Cyan) {
        Text(
            text = "Hi, my name is $name!",
            modifier = modifier.padding(24.dp)
        )
    }
}

@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    GreetingCardTheme { Greeting("YourName") }
}
```

---

## 8  Key Takeaways

* **Empty Activity** template → quickest path to a Compose screen.
* Use **Preview** to iterate without deploying.
* `@Composable` = UI building block; capitalized; no returns.
* **Surface + Color** customize container appearance.
* **Modifier** chain for padding, size, borders, etc.

### Next Steps

* Run on **Emulator** or physical device.
* Explore layout primitives (`Row`, `Column`, `Box`).

---

## Learn More

* [Meet Android Studio](https://developer.android.com/studio/intro)
* [Create a Project](https://developer.android.com/studio/projects/create-project)
* [Jetpack Compose Basics](https://developer.android.com/jetpack/compose)
* [Material 3 Padding](https://m3.material.io/foundations/layout/applying-layout/window-size-classes)
