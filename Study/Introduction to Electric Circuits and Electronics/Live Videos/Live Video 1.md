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
![[Pasted image 20250601225814.png]]

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
![[Pasted image 20250601225841.png]]
![[Pasted image 20250601225909.png]]
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
![[Pasted image 20250601230502.png]]
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
![[Pasted image 20250601230517.png]]
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

# Solved Problem Set

This file gives the **step‑by‑step algebra** behind each question shown in the live‑lecture slides so you can trace every conversion and calculation on paper.

---

## Question 2  Ohm’s‑Law Drill

> *Solve for the unknown quantity ($V, I, R$) given the other two; express answers in scientific and metric‑prefix notation.*

| a | **Given**: $I = 20\,\text{mA} = 20\times10^{-3}\,\text{A}$; $R = 5\,\text{kΩ} = 5\times10^{3}\,\text{Ω}$ |
| - | -------------------------------------------------------------------------------------------------------- |
|   | **Formula**: $V = IR$                                                                                    |
|   | $V = (20\times10^{-3})(5\times10^{3}) = 100\,\text{V} = 1.0\times10^{2}\,\text{V}$                       |

\| b | **Given**: $I = 150\,µ\text{A} = 1.50\times10^{-4}\,\text{A};\; R = 47\,\text{kΩ} = 4.7\times10^{4}\,\text{Ω}$  |
\|   | $V = IR = (1.50\times10^{-4})(4.7\times10^{4}) = 7.05\,\text{V} = 7.05\times10^{0}\,\text{V}$ |

\| c | **Given**: $V = 24\,\text{V};\; R = 3.3\,\text{MΩ} = 3.3\times10^{6}\,\text{Ω}$ |
\|   | $I = V/R = \dfrac{24}{3.3\times10^{6}} = 7.27\times10^{-6}\,\text{A} = 7.27\,µ\text{A}$ |

\| d | **Given**: $V = 7.2\,\text{kV} = 7.2\times10^{3}\,\text{V};\; R = 900\,\text{Ω}$ |
\|   | $I = V/R = \dfrac{7.2\times10^{3}}{900} = 8.0\,\text{A} = 8.0\times10^{0}\,\text{A}$ |

\| e | **Given**: $V = 1.02\,\text{mV} = 1.02\times10^{-3}\,\text{V};\; I = 40\,µ\text{A} = 4.0\times10^{-5}\,\text{A}$ |
\|   | $R = V/I = \dfrac{1.02\times10^{-3}}{4.0\times10^{-5}} = 2.55\times10^{3}\,\text{Ω} = 2.55\,\text{kΩ}$ |

\| f | **Given**: $V = 3.5\,\text{GV} = 3.5\times10^{9}\,\text{V};\; I = 0.76\,µ\text{A} = 7.6\times10^{-7}\,\text{A}$ |
\|   | $R = V/I = \dfrac{3.5\times10^{9}}{7.6\times10^{-7}} = 4.6\times10^{15}\,\text{Ω} = 46\,\text{PΩ}$ |

---

## Kirchhoff’s Current Law (KCL)

### Conceptual Node Example (slide diagram)

Assume arrows **into** node are positive.

$$
I_1 + I_2 + I_3 + I_4 - I_5 = 0
$$

Re‑arrange for any unknown current.

### Numeric Node Example

Given in slide: $I_1 = 10\,\text{A}$ (into node), $I_3 = 3\,\text{A}$ (out of node), solve for $I_2$ (out of node).

$$
I_1 - I_2 - I_3 = 0 \;\Rightarrow\; I_2 = I_1 - I_3 = 10 - 3 = 7\,\text{A}
$$

---

## Kirchhoff’s Voltage Law (KVL) Loop Example

Clockwise voltages taken as positive. Suppose you have one supply $E = 6\,\text{V}$ and three drops $V_1 = 1.5\,\text{V},\; V_2 = 2.2\,\text{V},\; V_3 = ?$.

$$
+E + V_1 + V_2 + V_3 = 0 \quad\Rightarrow\quad V_3 = -(E + V_1 + V_2) = -(6 + 1.5 + 2.2) = -9.7\,\text{V}
$$

The sign tells you the assumed polarity around the loop was opposite to reality.

---

## Question 3  Parallel‑Sources Circuit

> **Task:** Using nodal analysis, find (a) current through the 1.5 V battery, (b) current through the 100 Ω resistor, (c) current through the 200 Ω resistor and 9 V source, and (d) power dissipated by the 100 Ω resistor.

**Warning:** Placing unequal ideal voltage sources in parallel is *physically inconsistent* (infinite circulating current). Classroom slides imply hidden internal resistances. We assume 1 Ω internal resistance per source to keep numbers finite.

### 1  Define Node Voltage

Let the lower conductor be reference (0 V) and the top conductor be node $V$.

### 2  Branch Currents (downward positive)

$$
\begin{aligned}
I_{1.5}&=\dfrac{V-1.5}{1}\quad (1.5\,\text{V source})\\[3pt]
I_{100}&=\dfrac{V}{100}\\[3pt]
I_{9}&=\dfrac{V-9}{201}\quad (9\,\text{V}+200\,\Omega)\end{aligned}
$$

### 3  Apply KCL: Σ currents = 0

$$
(V-1.5) + \frac{V}{100} + \frac{V-9}{201} = 0
$$

Multiply by the common denominator 20 100 → 201 00 to avoid fractions (or solve directly):

$$
(20100)(V-1.5) + 201(V) + 100(V-9) = 0
$$

$$
20100V - 30150 + 201V + 100V - 900 = 0
$$

$$
20401V = 31050 \;\Rightarrow\; V \approx 1.57\,\text{V}
$$

### 4  Compute Branch Currents

| Branch    | Expression     | Value        | Direction                                         |
| --------- | -------------- | ------------ | ------------------------------------------------- |
| 1.5 V     | $(1.57-1.5)/1$ | **+0.07 A**  | *down* toward battery (battery **absorbs** 70 mA) |
| 100 Ω     | $1.57/100$     | **15.7 mA**  | down                                              |
| 9 V+200 Ω | $(1.57-9)/201$ | **−15.6 mA** | up (i.e., into 9 V source)                        |

Currents satisfy KCL to rounding error.

### 5  Power in 100 Ω Resistor

$$
P = I^2R = (0.0157)^2 \times 100 \approx 2.46\times10^{-2}\,\text{W} \approx 25\,\text{mW}
$$

---

### What if the Sources Were Ideal (R\_int = 0)?

KCL would reduce to $V = 1.5$ and $V = 9$ simultaneously ⇒ contradiction ⇒ infinite circulating current. Real circuits avoid this by never hard‑wiring unequal ideal sources in parallel.

---

## ✅ Summary Checklist

* [x] Converted every prefix to base SI units before plugging into formulas.
* [x] Applied **Ohm’s Law** correctly.
* [x] Demonstrated **KCL** at an abstract node and on a numeric circuit.
* [x] Demonstrated **KVL** around a single‑loop circuit.
* [x] Performed nodal analysis on the parallel‑source challenge.
