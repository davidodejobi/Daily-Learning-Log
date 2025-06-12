# Week 11: GUI Components & Layout Management – Comprehensive Notes

## 🎯 Learning Objectives

* Identify **common GUI components** (buttons, labels, text fields, etc.) and their roles.
* Describe how **layout managers** arrange components inside a window.
* Compare **BorderLayout, FlowLayout, GridLayout**, and know when to use each.
* Understand strategies for **custom GUI components** (extending, composing, or building from scratch).
* Articulate the **advantages of GUIs** over hard‑coded/CLI approaches.

---

## 1  Introduction – Why GUIs Matter

A **Graphical User Interface** provides a visual, interactive layer that allows users to click, type, or drag instead of memorising commands. Well‑designed GUIs increase accessibility, reduce errors, and improve user satisfaction in modern software.

---

## 2  Common GUI Components (Widgets)

| Component                 | Iconic Use‑Cases                    | Key Properties & Tips                                                                                    |
| ------------------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Button**                | Start, Submit, Navigation           | Emits a *clicked* signal; provide visual feedback (hover/press); set `setDefault(true)` for main action. |
| **Label**                 | Static text, images, captions       | Non‑interactive; use `setWordWrap(true)` for paragraphs; rich‑text (HTML) for styling.                   |
| **Text Field / LineEdit** | Single‑line input (login, search)   | Add `QValidator` for numeric/regex input; placeholder text guides user.                                  |
| **Text Area**             | Multi‑line notes, logs              | `QPlainTextEdit` for plain text, `QTextEdit` for rich text.                                              |
| **Combo Box**             | Choose from list (country, font)    | `setEditable(true)` for hybrid combo/search; populate via `addItem` or model.                            |
| **Check Box**             | Boolean options (remember me)       | Tri‑state (`Qt::PartiallyChecked`) for parent/child lists.                                               |
| **Radio Button**          | Mutually‑exclusive choices (gender) | Group with `QButtonGroup` to enforce exclusivity.                                                        |
| **Slider / Dial**         | Continuous value (volume)           | Map linear value to log scale for audio volume.                                                          |
| **Progress Bar**          | Task progress                       | Use `setRange(0,0)` for busy/indeterminate state.                                                        |

> 🔎 **Worksheet Q1 recap:** *Button* triggers an action; *Label* just displays information.

---

## 3  Layout Management – Arranging Components

Absolute positioning breaks on resize or different DPI. **Layout managers** compute widget geometry dynamically.

| Layout Manager   | How It Works                                                               | Best For                                                            | Weaknesses                                          |
| ---------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------- | --------------------------------------------------- |
| **BorderLayout** | Divides container into five regions: **North, South, East, West, Centre**. | Classic desktop windows: central canvas with menus/toolbars around. | Rigid – only five slots; centre must stretch.       |
| **FlowLayout**   | Places widgets left‑to‑right (or top‑to‑bottom) and wraps like text.       | Toolbars, tag clouds, dynamic chip lists.                           | Alignment control limited; uneven lines possible.   |
| **GridLayout**   | Matrix of equal cells; widgets can span rows/cols.                         | Calculators, data‑entry forms, dashboards.                          | All cells equal unless spans used; may waste space. |

### 3.1 Two Scenarios for **GridLayout** (Worksheet Q3)

1. **Calculator keypad** – uniform buttons in 4×5 grid ensures neat alignment.
2. **Employee data form** – labels in column 0, fields in column 1 create tidy two‑column layout.

### 3.2 How Layout Managers Work Internally

1. Each widget reports **size hint & min/max**.
2. Layout iterates children, distributes available space.
3. Handles language direction (LTR/RTL) and high‑DPI scaling automatically.

---

## 4  Custom GUI Components

| Approach                   | When to Use                                      | Example                                                                       |
| -------------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------- |
| **Extend existing widget** | Need extra behaviour but same visual base        | Inherit `QPushButton` ➜ `ProgressButton` that shows spinning icon while busy. |
| **Compose widgets**        | Combine standard widgets into a compound control | `Label + ProgressBar` inside an `HBoxLayout` ➜ Status strip item.             |
| **Build from scratch**     | Highly specialised visuals/behaviour             | Custom OpenGL drawing canvas; override `paintEvent`.                          |

### Pros & Cons (Worksheet Q4)

* **Pros:** Tailored UX, reusable across projects, encapsulates logic.
* **Cons:** More code to test/maintain; risks breaking native look‑and‑feel; may need custom accessibility support.

---

## 5  Advantages of GUIs over Hard‑coded/CLI Interfaces

1. **User‑friendly** – discoverable commands via menus/buttons.
2. **Error prevention** – disable invalid options; validate input visually.
3. **Lower learning curve** – no memorisation; icons aid recognition.
4. **Visual feedback** – progress bars, colour cues, animations.
5. **Accessibility** – assistive tech integration, zoom, high‑contrast modes.
6. **Market appeal** – modern apps expected to have polished GUI.

---

## 6  Lesson Questions – Model Answers

1. **Text Field** allows entering/editing text (**Correct Answer: C**).
2. Layout manager’s role ➜ *arrange and position components* (**Correct Answer: D**).
3. GridLayout scenarios – see Section 3.1.
4. Advantages/disadvantages of custom components – see Section 4.

---

## 7  Practical Exercise (Optional)

Implement a **simple login window** in Qt:

1. `QGridLayout` with labels and line‑edits (username, password).
2. Add *Login* & *Cancel* buttons (horizontal `QHBoxLayout`).
3. Validate that fields are non‑empty; show `QMessageBox` on error.
4. Style with stylesheet for dark mode.
