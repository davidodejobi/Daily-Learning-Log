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

### Keep this sheet beside you while practising Ohm’s‑law drills!
