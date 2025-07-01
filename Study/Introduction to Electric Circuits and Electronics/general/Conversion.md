# Metric Prefix Conversion Cheat Sheet (PHY202)

*Purpose:* A quick‑reference table so you can instantly convert between SI base units and the common electrical prefixes you’ll meet in Ohm’s‑law problems.

---

## 1  Common Prefixes

| Prefix              | Symbol | Factor | Multiply by… |
| ------------------- | ------ | ------ | ------------ |
| **mega**            | M      | 10⁶    | 1 000 000    |
| **kilo**            | k      | 10³    | 1 000        |
| **–** *(base unit)* | –      | 10⁰    | 1            |
| **milli**           | m      | 10⁻³   | 0.001        |
| **micro**           | µ      | 10⁻⁶   | 0.000 001    |
| **nano**            | n      | 10⁻⁹   | 1 × 10⁻⁹     |

> **Tip:** Jumping two rows shifts ×10⁶ (e.g.
> k → µ is three orders of 10 so 10⁹).

---

## 2  Quick‑Convert Tables

### 2.1  Current (amperes)

| Value in A | mA       | µA            |
| ---------- | -------- | ------------- |
| 1 A        | 1 000 mA | 1 000 000 µA  |
| 0.020 A    | 20 mA    | 20 000 µA     |
| 150 µA     | 0.150 mA | 1.50 × 10⁻⁴ A |

### 2.2  Resistance (ohms)

| Ω       | kΩ       | MΩ          |
| ------- | -------- | ----------- |
| 5 000 Ω | 5 kΩ     | 0.005 MΩ    |
| 3.3 MΩ  | 3 300 kΩ | 3 300 000 Ω |

### 2.3  Voltage examples

| V      | mV       | kV        |
| ------ | -------- | --------- |
| 1.5 V  | 1 500 mV | 0.0015 kV |
| 7.2 kV | 7 200 V  | –         |

---

## 3  How to Convert — One‑Line Method

1. **Write the numerical value** in scientific notation:
      example 20 mA → 2.0 × 10¹ mA.
2. **Add the prefix exponent** (+3 for milli → base).
      2.0 × 10¹ × 10⁻³ A = 2.0 × 10⁻² A.
3. **Combine powers:** 10¹⁻³ = 10⁻².

Result: 20 mA = 0.020 A.

---

## 4  Mnemonic

"**King Henry Died *While* Drinking Chocolate Milk, µmmm nice**"
(kilo 10³, hecto 10², deka 10¹, *unit*, deci 10⁻¹, centi 10⁻², milli 10⁻³, **µ** 10⁻⁶, nano 10⁻⁹).  Skip unused steps — just remember *k → → m → µ*.

---

## 5  Practice Challenge

1. Convert 47 kΩ to ohms and mega‑ohms.
2. Express 0.76 A in mA and µA.
3. A multimeter reads 3.5 GV. What is this in kV?

*(Answers are hidden below — try first!)*

<details>
<summary>Show answers</summary>

1. 47 kΩ = 47 000 Ω = 0.047 MΩ
2. 0.76 A = 760 mA = 760 000 µA
3. 3.5 GV = 3 500 000 kV

</details>

---

# Metric Prefix Conversion Factors – Voltage, Current, Resistance (PHY202)

A single glance reference for quickly jumping between **volts (V)**, **amperes (A)**, and **ohms (Ω)** at the common engineering prefixes.

---

## 1. Core Prefixes

| Prefix       | Symbol | Factor (× base) | Shortcut        | Example ① Voltage      | Example ② Current      | Example ③ Resistance   |
| ------------ | ------ | --------------- | --------------- | ---------------------- | ---------------------- | ---------------------- |
| **giga**     | G      | 10⁹             | × 1 000 000 000 | 3 GV = 3 000 000 000 V | 0.5 GA = 500 000 000 A | 2 GΩ = 2 000 000 000 Ω |
| **mega**     | M      | 10⁶             | × 1 000 000     | 7 MV = 7 000 000 V     | 120 mA *(↷ see milli)* | 4.7 MΩ = 4 700 000 Ω   |
| **kilo**     | k      | 10³             | × 1 000         | 1.2 kV = 1 200 V       | 3 kA = 3 000 A         | 10 kΩ = 10 000 Ω       |
| **—** (unit) | —      | 1               | × 1             | 230 V (base)           | 2 A                    | 560 Ω                  |
| **milli**    | m      | 10⁻³            | ÷ 1 000         | 250 mV = 0.250 V       | 40 mA = 0.040 A        | 8.2 mΩ = 0.0082 Ω      |
| **micro**    | µ      | 10⁻⁶            | ÷ 1 000 000     | 750 µV = 0.000 750 V   | 130 µA = 0.000 130 A   | 50 µΩ = 0.000 050 Ω    |
| **nano**     | n      | 10⁻⁹            | ÷ 1 000 000 000 | 20 nV = 2×10⁻⁸ V       | 15 nA = 1.5×10⁻⁸ A     | 1 nΩ = 1×10⁻⁹ Ω        |

> **Mnemonic:** **G**reat **M**ighty **k**ings **— m**ight **µ**se **n**anotech
> (reading from G→n reminds you of descending powers of 1 000).

---

## 2. Quick‑Convert Rules

1. **Base → prefix**: multiply by its factor (e.g. 0.002 A × 10³ = 2 mA).
2. **Prefix → base**: divide by the same factor (e.g. 47 kΩ ÷ 10³ = 47 000 Ω).
3. **Prefix → another prefix**: move through base if unsure (e.g. 5 mA → A → µA).
4. Keep **3 significant figures** unless your problem specifies otherwise.

---

## 3. Mini‑Exercises (answers below)

Convert each quantity into the two units requested:

| # | Given  | Convert to | Result |
| - | ------ | ---------- | ------ |
| 1 | 18 mA  | A          | …      |
|   |        | µA         | …      |
| 2 | 2.4 kV | V          | …      |
|   |        | mV         | …      |
| 3 | 330 µΩ | Ω          | …      |
|   |        | kΩ         | …      |

<details><summary>Show Answers</summary>

1. 18 mA = 0.018 A ; 18 000 µA
2. 2.4 kV = 2 400 V ; 2 400 000 mV
3. 330 µΩ = 0.000 330 Ω ; 0.000 330 kΩ

</details>

---

### Why identical factors work for V, A, Ω

The metric system prefixes modify **any** SI base or derived unit by pure powers of ten. Whether you’re measuring potential difference (V), electric current (A), or resistance (Ω), the same ×10³, ×10⁶, ×10⁻³ … rules apply.

**Practice tip:** Write the powers‑of‑ten ladder on scrap paper and slide your decimal left/right in steps of three to build reflex speed.
