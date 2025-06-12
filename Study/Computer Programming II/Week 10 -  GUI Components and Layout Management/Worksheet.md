# Week 10 Worksheet – GUI Components & Layout Management

Below are the worksheet questions with concise, model answers for quick review.

---

## 1  Understanding GUI Components

List **three common GUI components** and describe their typical uses.

| Component                | Description                                             | Typical Use                                                  |
| ------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| **Button**               | Clickable control that generates an `action` event.     | Submitting a form, starting playback, opening a file dialog. |
| **Text Box / Line Edit** | Field where the user types text.                        | Entering a username, search query, or file path.             |
| **Label**                | Non‑editable text or icon, often used for instructions. | Field captions ("Username:"), status messages, logo display. |

---

## 2  Designing a Simple Music‑Player GUI

**Add two additional components** you might use and explain their purpose.

| Component                     | Purpose in Music Player                                  |
| ----------------------------- | -------------------------------------------------------- |
| **Slider (Seek Bar)**         | Shows track progress and lets user scrub to a timestamp. |
| **ListView / Playlist Panel** | Displays queue of songs; user selects track to play.     |

> Other possible components: **Volume slider**, **Play/Pause toggle button**, **Progress Label** (elapsed / total time).

---

## 3  Role of Layout Managers

> **Answer:** A layout manager automatically arranges GUI components within a container according to layout rules (grid, flow, border, etc.). This avoids manual pixel positioning, making the interface responsive to resizing and platform differences.

---

## 4  Match the Layout Managers

| Layout Manager   | Correct Description                                                                |
| ---------------- | ---------------------------------------------------------------------------------- |
| **BorderLayout** | Arranges components in five regions (north, south, east, west, centre).            |
| **FlowLayout**   | Arranges components in a single row/column, flowing to next line/column when full. |
| **GridLayout**   | Arranges components in a grid pattern with equal‑sized cells.                      |

---

## 5  Calculator Layout Sketch (Text Description)

**Chosen layout manager:** **GridLayout** (4 columns × 5 rows)

| Row | Components (left → right)                  |
| --- | ------------------------------------------ |
| 1   | Display `QLineEdit` spanning all 4 columns |
| 2   | `7  8  9  ÷`                               |
| 3   | `4  5  6  ×`                               |
| 4   | `1  2  3  −`                               |
| 5   | `0  .` (decimal) `=` `+`                   |

**Why GridLayout?** A calculator is a natural matrix of equally‑sized numeric and operator buttons. `GridLayout` ensures buttons align neatly and resize uniformly, while the display sits in the top row spanning the full width.

---

### Quick Recap

* **Buttons, text fields, labels** form the backbone of everyday GUIs.
* **Layout managers** free you from absolute coordinates, promoting responsive design.
* **Grid layouts** suit calculators and keypads; **Flow/Border layouts** suit toolbars and dashboards.
