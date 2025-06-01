## PHY202 – Live Video Note

> **Theme:** Foundations of Electric Circuits – DC vs AC behaviour, core components, fundamental laws, and everyday applications.

---

## 1  Why Electric Circuits Matter

Modern life runs on well‑behaved electrons. From a Bluetooth speaker that suddenly goes silent to the power system of a spacecraft, **every fault ultimately traces back to a circuit problem**. Understanding how charge flows through simple elements (resistors, capacitors, inductors, transistors) is therefore the first step toward becoming an electronics‑literate engineer.

---

## 2  Types of Current

### 2.1  Direct Current (DC)

| Property              | Description                                                                                                                                           |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**        | Current flows **in one direction only**; voltage remains (approximately) constant.                                                                    |
| **Generation**        | • *Commutated* DC generator  ↠ mechanical AC → DC <br>• **Rectifier** converts AC mains to DC <br>• **Batteries** perform electro‑chemical conversion |
| **Water Analogy**     | A raised water tank that can push water one way until the tank is empty.                                                                              |
| **Graph**             | Flat line (e.g. 1.5 V battery) → $V(t)=\;1.5\,\text{V}$.                                                                                              |
| **Typical Home Uses** | Cell‑phones, TVs (AC mains internally rectified), flashlights, hybrid & electric cars                                                                 |

### 2.2  Alternating Current (AC)

| Property              | Description                                                                                                                              |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**        | Charge **reverses direction periodically**; voltage also reverses.                                                                       |
| **Mathematical Form** | $V(t)=V_{\text{P}}\,\sin\bigl(2\pi f t + \varphi\bigr)$                                                                                  |
|                       | • $V_{\text{P}}$ = peak amplitude <br>• $f$ = frequency \[Hz] <br>• $\varphi$ = phase \[° or rad] <br>• $2\pi$ converts cycles → radians |
| **Water Analogy**     | A piston continuously pushes and pulls water back and forth in the pipe.                                                                 |
| **Typical Home Uses** | Refrigerators, ovens, washing machines, lighting (LED / incandescent), HVAC systems                                                      |

### 2.3  Quick Comparison

| Feature           | **DC**                                | **AC**                                           |
| ----------------- | ------------------------------------- | ------------------------------------------------ |
| Direction of flow | Uni‑directional                       | Alternates                                       |
| Waveform          | Constant (or slowly varying)          | Sinusoidal (or other periodic)                   |
| Transmission      | Short distances / electronic circuits | Long‑distance power grids (transformer friendly) |
| Storage           | Batteries, super‑caps                 | Requires conversion to store                     |

---

## 3  Electric Circuit Fundamentals

> **Electric circuit = closed conducting loop that allows current to pass.**

### 3.1  Key Components & Roles

* **Conductors (Wires)** – provide the low‑resistance path.
* **Switches** – open/close the loop, controlling current.
* **Power Sources** – batteries, generators supply EMF (E).
* **Resistors (R)** – limit current & set voltage drops.
* **Capacitors (C)** – store / release electric field energy.
* **Inductors (L)** – store energy in magnetic field; oppose changes in current.

### 3.2  Common Schematic Symbols

```
wire        ────────          junction        ─•─
wire (no jn) ───┬──            resistor        ─[ ]─
variable R  ─[⊘]─              capacitor       ─||─
inductor     ─(coil)─         switch (open)   ─o/ o─
lamp/load    ─(⌀)─
```

![[Pasted image 20250601223410.png]]

---

## 4  Fundamental Laws

### 4.1  Ohm’s Law

> The current $I$ through a conductor is **directly proportional** to the applied voltage $V$ and **inversely proportional** to its resistance $R$:
> $\displaystyle I = \frac{V}{R}$

Triangle mnemonic:

```
      V
    ────
    I │ R
```

Therefore also $V = I R$ and $R = V / I$.

### 4.2  Kirchhoff’s Laws

1. **KCL (Current Law)** – Sum of currents entering a node = sum leaving (charge conservation).
2. **KVL (Voltage Law)** – Algebraic sum of voltages around any closed loop = 0 (energy conservation).

These are the foundation for mesh‑current and node‑voltage analysis you will meet in coming weeks.

---

## 5  Learning Objectives & Outcomes (Week 1)

By the end of this week you should be able to:

1. **Distinguish** between D.C. and A.C. circuits, citing real‑world examples.
2. **Explain** and apply Ohm’s Law for simple resistive circuits.
3. **Identify** common circuit elements and their schematic symbols.
4. **Interpret** the sine‑wave equation $V(t)=V_P\sin(2\pi f t + \varphi)$ and relate each parameter to waveform characteristics.
5. **Summarise** everyday applications of AC & DC in households.

---

### 📌 Pro‑Tips for Study

* Memorise the sine‑wave formula and practise calculating **period**, **frequency**, and **phase shift**.
* Draw a blank circuit diagram and challenge yourself to label each symbol from memory.
* Use the Ohm’s‑Law triangle to quickly rearrange formulas in quiz settings.

# PHY202 – Week 1 Detailed Lecture Notes

> **Theme:** Foundations of Electric Circuits – DC vs AC behaviour, core components, fundamental laws, and everyday applications.

---

## 1  Why Electric Circuits Matter

Modern life runs on well‑behaved electrons. From a Bluetooth speaker that suddenly goes silent to the power system of a spacecraft, **every fault ultimately traces back to a circuit problem**. Understanding how charge flows through simple elements (resistors, capacitors, inductors, transistors) is therefore the first step toward becoming an electronics‑literate engineer.

---

## 2  Types of Current

### 2.1  Direct Current (DC)

| Property              | Description                                                                                                                                           |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**        | Current flows **in one direction only**; voltage remains (approximately) constant.                                                                    |
| **Generation**        | • *Commutated* DC generator  ↠ mechanical AC → DC <br>• **Rectifier** converts AC mains to DC <br>• **Batteries** perform electro‑chemical conversion |
| **Water Analogy**     | A raised water tank that can push water one way until the tank is empty.                                                                              |
| **Graph**             | Flat line (e.g. 1.5 V battery) → $V(t)=\;1.5\,\text{V}$.                                                                                              |
| **Typical Home Uses** | Cell‑phones, TVs (AC mains internally rectified), flashlights, hybrid & electric cars                                                                 |

### 2.2  Alternating Current (AC)

| Property              | Description                                                                                                                              |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**        | Charge **reverses direction periodically**; voltage also reverses.                                                                       |
| **Mathematical Form** | $V(t)=V_{\text{P}}\,\sin\bigl(2\pi f t + \varphi\bigr)$                                                                                  |
|                       | • $V_{\text{P}}$ = peak amplitude <br>• $f$ = frequency \[Hz] <br>• $\varphi$ = phase \[° or rad] <br>• $2\pi$ converts cycles → radians |
| **Water Analogy**     | A piston continuously pushes and pulls water back and forth in the pipe.                                                                 |
| **Typical Home Uses** | Refrigerators, ovens, washing machines, lighting (LED / incandescent), HVAC systems                                                      |

### 2.3  Quick Comparison

| Feature           | **DC**                                | **AC**                                           |
| ----------------- | ------------------------------------- | ------------------------------------------------ |
| Direction of flow | Uni‑directional                       | Alternates                                       |
| Waveform          | Constant (or slowly varying)          | Sinusoidal (or other periodic)                   |
| Transmission      | Short distances / electronic circuits | Long‑distance power grids (transformer friendly) |
| Storage           | Batteries, super‑caps                 | Requires conversion to store                     |

---

## 3  Electric Circuit Fundamentals

> **Electric circuit = closed conducting loop that allows current to pass.**

### 3.1  Key Components & Roles

* **Conductors (Wires)** – provide the low‑resistance path.
* **Switches** – open/close the loop, controlling current.
* **Power Sources** – batteries, generators supply EMF (E).
* **Resistors (R)** – limit current & set voltage drops.
* **Capacitors (C)** – store / release electric field energy.
* **Inductors (L)** – store energy in magnetic field; oppose changes in current.

### 3.2  Common Schematic Symbols

```
wire        ────────          junction        ─•─
wire (no jn) ───┬──            resistor        ─[ ]─
variable R  ─[⊘]─              capacitor       ─||─
inductor     ─(coil)─         switch (open)   ─o/ o─
lamp/load    ─(⌀)─
```

*(Refer to slide for visual versions.)*

---

## 4  Fundamental Laws

### 4.1  Ohm’s Law

> The current $I$ through a conductor is **directly proportional** to the applied voltage $V$ and **inversely proportional** to its resistance $R$:
> $\displaystyle I = \frac{V}{R}$

Triangle mnemonic:

```
      V
    ────
    I │ R
```

Therefore also $V = I R$ and $R = V / I$.

### 4.2  Kirchhoff’s Laws

1. **KCL (Current Law)** – Sum of currents entering a node = sum leaving (charge conservation).
2. **KVL (Voltage Law)** – Algebraic sum of voltages around any closed loop = 0 (energy conservation).

These are the foundation for mesh‑current and node‑voltage analysis you will meet in coming weeks.

---

## 5  Learning Objectives & Outcomes (Week 1)

By the end of this week you should be able to:

1. **Distinguish** between D.C. and A.C. circuits, citing real‑world examples.
2. **Explain** and apply Ohm’s Law for simple resistive circuits.
3. **Identify** common circuit elements and their schematic symbols.
4. **Interpret** the sine‑wave equation $V(t)=V_P\sin(2\pi f t + \varphi)$ and relate each parameter to waveform characteristics.
5. **Summarise** everyday applications of AC & DC in households.

---

### 📌 Pro‑Tips for Study

* Memorise the sine‑wave formula and practise calculating **period**, **frequency**, and **phase shift**.
* Draw a blank circuit diagram and challenge yourself to label each symbol from memory.
* Use the Ohm’s‑Law triangle to quickly rearrange formulas in quiz settings.

---

\*End of Week 1 notes.

---

## 6  Worked Examples

### 6.1  Ohm’s Law Practice Set

Solve for the missing quantity in each pair and present answers in **scientific** and **metric‑prefix** notation.

| # | Given                   | Unknown | Formula   | Scientific    | Metric  |
| - | ----------------------- | ------- | --------- | ------------- | ------- |
| a | I = 20 mA, R = 5 kΩ     | V       | V = I × R | 1.0 × 10² V   | 100 V   |
| b | I = 150 µA, R = 47 kΩ   | V       | V = I × R | 7.05 × 10⁰ V  | 7.05 V  |
| c | V = 24 V, R = 3.3 MΩ    | I       | I = V / R | 7.27 × 10⁻⁶ A | 7.27 µA |
| d | V = 7.2 kV, R = 900 Ω   | I       | I = V / R | 8.0 × 10⁰ A   | 8 A     |
| e | V = 1.02 mV, I = 40 µA  | R       | R = V / I | 2.55 × 10³ Ω  | 2.55 kΩ |
| f | V = 3.5 GV, I = 0.76 µA | R       | R = V / I | 4.6 × 10¹⁶ Ω  | 46 PΩ   |

> **Tip:** Convert everything to base SI units (A, V, Ω) *before* applying Ohm’s law, then reconvert to the most convenient prefix.

---

### 6.2  Kirchhoff’s Current Law (KCL)

**Statement:** The algebraic sum of currents entering and leaving any node is zero.

**Symbolic form:** I₁ + I₂ + I₃ + I₄ − I₅ = 0

**Numeric slide example:** If I₁ = 10 A enters and I₃ = 3 A leaves, then
I₂ = I₁ − I₃ = 10 A − 3 A = 7 A (leaving the node).

---

### 6.3  Kirchhoff’s Voltage Law (KVL)

**Statement:** The algebraic sum of voltages around any closed loop is zero.

Example with a 6 V source and three drops V₁ (1.5 V), V₂ (2.2 V), V₃ (?):
E + V₁ + V₂ + V₃ = 0  ⇒  V₃ = −(6 + 1.5 + 2.2) = −9.7 V.  The minus sign indicates the assumed polarity is opposite to the actual.

---

### 6.4  Challenge Circuit (Parallel Sources)

**Setup (slide “Question 3”):** Three parallel branches between common nodes

| Branch | Elements                                  |
| ------ | ----------------------------------------- |
| A      | 1.5 V ideal battery                       |
| B      | 100 Ω resistor                            |
| C      | 9 V battery in series with 200 Ω resistor |

Ideal sources of unequal voltage should not be placed directly in parallel. One classroom workaround is to assume each source has a small internal resistance (e.g., 1 Ω) and solve using nodal analysis.

Let node voltage = V (bottom node is 0 V).

| Branch | Current (downwards taken positive) |
| ------ | ---------------------------------- |
| A      | (V − 1.5) / 1 Ω                    |
| B      | V / 100 Ω                          |
| C      | (V − 9) / 201 Ω                    |

Apply **KCL**: (V − 1.5) + V/100 + (V − 9)/201 = 0.

Solving gives V ≈ 1.57 V.

Currents:

| Branch      | Current   | Interpretation                    |
| ----------- | --------- | --------------------------------- |
| 1.5 V       | −0.07 A   | 70 mA into battery (charging)     |
| 100 Ω       | +0.0157 A | 15.7 mA downward                  |
| 9 V + 200 Ω | −0.0156 A | 15.6 mA upward (battery charging) |

Power dissipated by the 100 Ω resistor:
P = I²R ≈ (0.0157 A)² × 100 Ω ≈ 0.025 W.