# SwiftUI Essentials: Using Stacks to Arrange Views

### Goal

Build a meeting‑timer screen (Scrumdinger) while mastering `HStack`, `VStack`, `ZStack`, view modifiers, and accessibility patterns.

## Reference – Key Enums & Parameters

### Stack Alignment

* **`HStack`**: `.top`, `.center`, `.bottom`, `.firstTextBaseline`, `.lastTextBaseline`
* **`VStack`**: `.leading`, `.center`, `.trailing`, `.firstTextBaseline`, `.lastTextBaseline`
* **`ZStack`**: `.topLeading`, `.top`, `.topTrailing`, `.leading`, `.center`, `.trailing`, `.bottomLeading`, `.bottom`, `.bottomTrailing`

### ProgressViewStyle

* `.linear`
* `.circular`
* `.automatic` (platform‑adaptive)

### Font Presets (`Font`)

`.largeTitle`, `.title`, `.title2`, `.title3`, `.headline`, `.subheadline`, `.body`, `.callout`, `.caption`, `.caption2`, `.footnote`

### Button Roles

* `.none` (default)
* `.cancel`
* `.destructive`

### StrokeStyle

`lineWidth`, `lineCap` (`.butt`, `.round`, `.square`), `lineJoin` (`.miter`, `.round`, `.bevel`), `miterLimit`, `dash`, `dashPhase`

### Label Initialisers

* `Label(_ title: String, systemImage: String)`
* `Label(title: Image, icon: Image)`
* `Label(title: () -> Text, icon: () -> Image)`

### Accessibility Traits (common)

`.isButton`, `.isHeader`, `.isLink`, `.updatesFrequently`, `.isSelected`, `.isKey`, `.isStaticText`, `.isSummaryElement`

### Spacer

`Spacer(minLength: CGFloat?)` – specify a minimum or leave `nil` for system default.

---

## 1. Why Stacks?

SwiftUI lays out views by *composition*. Stacks let you group views in three principal axes:

* **`HStack`** – horizontal (left → right in LTR locales).
* **`VStack`** – vertical (top → bottom).
* **`ZStack`** – depth (back → front), useful for overlays.
  Using stacks instead of fixed coordinates means layouts adapt automatically to different screen sizes, accessibility settings, and localisation.

## 2. Anatomy of a Stack

```swift
HStack(alignment: .center, spacing: 8) {
    /* child views */
}
```

* **Alignment** – how children align along the *cross‑axis* (e.g. `.top` in an `HStack`).
* **Spacing** – fixed or `nil` (system default).
* **Child order** – reading order matters for both layout and accessibility.

## 3. Core Layout Modifiers

| Modifier                                              | Purpose                                                        |
| ----------------------------------------------------- | -------------------------------------------------------------- |
| `.padding([.horizontal], 16)`                         | Adds system‑resolved insets.                                   |
| `.frame(width:height:alignment:)`                     | Offers explicit sizing.                                        |
| `.font(.caption)`                                     | Applies a text style; inherited by children unless overridden. |
| `.background(_:)` / `.overlay(_:)`                    | Layer decoration inside a `ZStack`.                            |
| `.accessibilityLabel(_:)` / `.accessibilityValue(_:)` | Improves assistive technology output.                          |

## 4. Building the Timer Header Step‑by‑Step

1. **Progress ring** – a linear progress bar showing elapsed vs. total time.
2. **Time labels** – grouped inside an `HStack` → two `VStack`s → `Text` + `Label`.
3. **Spacing & Alignment** – add `Spacer()` and set `.leading` / `.trailing` on the vertical stacks.
4. **Typography** – `.font(.caption)` for secondary text size.

```swift
VStack {
    ProgressView(value: 5, total: 15)

    HStack {
        VStack(alignment: .leading) {
            Text("Seconds Elapsed").font(.caption)
            Label("300", systemImage: "hourglass.tophalf.fill")
        }
        Spacer()
        VStack(alignment: .trailing) {
            Text("Seconds Remaining").font(.caption)
            Label("600", systemImage: "hourglass.bottomhalf.fill")
        }
    }
}
```

## 5. Completing the Timer Screen

Add a circular progress ring, footer, and padding:

```swift
Circle()
    .strokeBorder(lineWidth: 24)
    .frame(height: 260)

HStack {
    Text("Speaker 1 of 3")
    Spacer()
    Button(action: {}) { Image(systemName: "forward.fill") }
}
.padding()
```

## 6. Deeper Dive – Dynamic Timer Example

Below is a richer, self‑contained `MeetingView` demonstrating state, animation, and accessibility:

```swift
struct MeetingView: View {
    // MARK: – State
    @State private var elapsed: Int = 0
    let total: Int = 900 // 15 minutes

    var body: some View {
        VStack(spacing: 24) {
            // Linear progress
            ProgressView(value: Double(elapsed), total: Double(total))
                .progressViewStyle(.linear)

            // Time header
            HStack {
                VStack(alignment: .leading) {
                    Text("Seconds Elapsed").font(.caption)
                    Label("\(elapsed)", systemImage: "hourglass.tophalf.fill")
                }
                Spacer()
                VStack(alignment: .trailing) {
                    Text("Seconds Remaining").font(.caption)
                    Label("\(total - elapsed)", systemImage: "hourglass.bottomhalf.fill")
                }
            }
            .accessibilityElement(children: .ignore)
            .accessibilityLabel("Time remaining")
            .accessibilityValue("\((total - elapsed) / 60) minutes")

            // Circular timer
            ZStack {
                Circle()
                    .stroke(Color.secondary.opacity(0.2), lineWidth: 24)
                Circle()
                    .trim(from: 0, to: CGFloat(elapsed) / CGFloat(total))
                    .stroke(.indigo, style: StrokeStyle(lineWidth: 24, lineCap: .round))
                    .rotationEffect(.degrees(-90))
                    .animation(.easeInOut, value: elapsed)
            }
            .frame(width: 260, height: 260)

            // Footer controls
            HStack {
                Text("Speaker 1 of 3")
                Spacer()
                Button(action: advanceSpeaker) {
                    Image(systemName: "forward.fill")
                }
                .accessibilityLabel("Next speaker")
            }
        }
        .padding()
        .onReceive(timer) { _ in
            guard elapsed < total else { return }
            elapsed += 1
        }
    }

    // MARK: – Private
    private var timer: Publishers.Autoconnect<Timer.TimerPublisher> {
        Timer.publish(every: 1, on: .main, in: .common).autoconnect()
    }

    private func advanceSpeaker() {
        // handle speaker advancement here
    }
}
```

### What to Notice

* `Circle().trim(from:to:)` + rotation makes an **angular progress ring**.
* `@State` keeps UI and data in sync.
* A `Timer` publisher drives the countdown.
* Accessibility data is summarised on the header; repeated child values are ignored.

## 7. Extracting Reusable Components

Break large views into smaller pieces for clarity and testability:

```swift
struct TimeLabel: View {
    let title: String
    let value: Int
    let symbol: String
    let alignment: HorizontalAlignment

    var body: some View {
        VStack(alignment: alignment) {
            Text(title).font(.caption)
            Label("\(value)", systemImage: symbol)
        }
    }
}
```

Reuse in the header: `TimeLabel(title: "Seconds Elapsed", value: elapsed, symbol: "hourglass.tophalf.fill", alignment: .leading)`.

## 8. Performance & Best Practices

* **Lazy Stacks** (`LazyVStack`, `LazyHStack`) defer layout until a view becomes visible—ideal for lists.
* **State hoisting** – keep mutable state at the lowest common ancestor to avoid unnecessary updates.
* Prefer **fixed spacing values** only when needed; default nil spacing adapts to platform conventions.

## 9. Next Steps

1. Bind the timer to real meeting data (elapsed, total, speakers).
2. Localise strings with `Localizable.strings` and `.leading/.trailing` alignments.
3. Persist meeting history using `@AppStorage` or Core Data.
4. Add unit tests around the meeting‑timer logic.

---

### Further Reading

* *SwiftUI Essentials* (Apple Developer Documentation)
* *Hacking with Swift – 100 Days of SwiftUI* (Paul Hudson)
* WWDC23 – *What’s new in SwiftUI*
