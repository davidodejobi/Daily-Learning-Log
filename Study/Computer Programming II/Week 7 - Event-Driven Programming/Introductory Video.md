# Week 7: Event‑Driven & Asynchronous Programming – Detailed Study Notes

## 🎯 Learning Objectives

* Define **events** in software and explain why they matter.
* Describe the **event‑driven programming** model and its advantages over sequential flow.
* Explain **event‑handling methods**, **event propagation** (capturing/bubbling), and **asynchronous programming**.
* Recognise real‑world use‑cases (desktop UI, web apps, network I/O).

---

## 1  What Is an Event?

An **event** is any action or occurrence that a software system can detect and respond to, e.g. user clicks, keystrokes, timer ticks, server responses.

### Everyday Analogy

Just as a birthday or graduation triggers many human actions (dressing, photos), program events trigger code execution.

---

## 2  Event‑Driven Programming (EDP)

> **Definition:** A paradigm where program flow is determined by events rather than a fixed sequence of instructions.

### 2.1 Core Components

| Concept                      | Role                                                                     |
| ---------------------------- | ------------------------------------------------------------------------ |
| **Event Source**             | Object or subsystem where the event originates (button, timer, socket).  |
| **Event Object**             | Data structure describing the event (type, timestamp, payload).          |
| **Event Handler / Listener** | Function or method registered to react when that event occurs.           |
| **Event Loop / Dispatcher**  | Runtime mechanism that waits for events and dispatches them to handlers. |

### 2.2 Benefits

* Natural fit for **GUIs** & **IoT devices** (react to user or sensor input).
* Improves **responsiveness**; idle until something happens.
* Encourages **loose coupling**—components communicate via events.

---

## 3  Event‑Handling Methods

Special functions bound to an event type on a target object.

**Pseudo‑example (C++/Qt‑style):**

```cpp
connect(addButton, &QPushButton::clicked, this, &Calculator::handleAddClick);

void Calculator::handleAddClick() {
    double a = ui->inputA->value();
    double b = ui->inputB->value();
    ui->result->setText(QString::number(a + b));
}
```

When *addButton* emits **clicked**, Qt calls `handleAddClick` automatically.

---

## 4  Event Propagation (Web DOM example)

In hierarchical UIs (HTML elements, nested widgets) an event travels through **three** phases:

1. **Capturing** – from root down to target (rarely used).
2. **Target** – event handled on the element itself.
3. **Bubbling** – if not stopped, event moves upward to ancestors.

```html
<div id="container">
  <button id="btn">Add</button>
</div>
<script>
container.addEventListener('click', () => console.log('Container clicked'));
btn.addEventListener('click', e => {
  console.log('Button clicked');
  // e.stopPropagation();  // Uncomment to prevent bubbling
});
</script>
```

Sequence: **Button clicked** → (bubbles) → **Container clicked**.

---

## 5  Asynchronous Programming & Events

Traditional synchronous code blocks until a task finishes. **Async** code initiates a task and continues, handling the result via an event/callback when ready.

### 5.1 Common Mechanisms

| Language   | Mechanism                                      |
| ---------- | ---------------------------------------------- |
| JavaScript | Callbacks, **Promises**, `async/await`         |
| C++ (Qt)   | Signals & slots, `QFuture`, coroutines (C++20) |
| Python     | `asyncio`, `await`, callbacks                  |

### 5.2 Example (JS fetch)

```js
fetch('/api/orders')             // start request (non‑blocking)
  .then(resp => resp.json())     // promise resolves when data ready
  .then(data => renderTable(data))
  .catch(err => console.error(err));
```

While awaiting the server, the browser can process UI events; when the network reply arrives, a **promise‑resolved** event triggers the handler.

---

## 6  Use‑Cases of Event‑Driven & Async Models

* **GUI Applications** (desktop, web, mobile): clicks, keypresses, gestures.
* **Real‑time games**: render loop reacts to input & physics events.
* **Networking / Servers**: non‑blocking I/O, websockets, Node.js.
* **Embedded & IoT**: sensor interrupts, timer events.

---

## 7  Key Differences: Synchronous vs Asynchronous

| Property       | Synchronous                  | Asynchronous                                |
| -------------- | ---------------------------- | ------------------------------------------- |
| Execution flow | Sequential, blocking         | Non‑blocking; continues while waiting       |
| Responsiveness | UI freezes during long tasks | UI remains interactive                      |
| Complexity     | Simpler logic                | Requires callbacks/promises, error handling |
| Typical use    | Quick computations           | I/O, timers, network, file access           |

---

## 8  Best Practices

1. **Keep handlers short** – avoid long‑running work inside UI thread.
2. **Debounce/throttle** high‑frequency events (scroll, resize).
3. Use **stopPropagation / stopImmediatePropagation** wisely in the DOM.
4. In async code, handle errors (`catch`, `try/await`) to avoid silent failures.
5. Clean up listeners to prevent memory leaks (e.g., `removeEventListener`).

---

## 📌 Takeaways

* Events are central to interactive software.
* Event‑driven programming reacts to occurrences instead of linear steps.
* Event propagation lets handlers coexist at multiple hierarchy levels.
* Asynchronous programming works hand‑in‑hand with events to keep applications responsive.
