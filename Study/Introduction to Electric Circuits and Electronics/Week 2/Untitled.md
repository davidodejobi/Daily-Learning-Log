# PHY202 – Week 2 Lecture Notes

> **Theme:** Core circuit laws — Ohm’s Law, node/branch/loop terminology, and Kirchhoff’s Current & Voltage Laws (KCL, KVL) with worked examples.

---

## 1  Why Circuit Laws Matter

Understanding electrical circuits hinges on a small set of universal rules. These laws let us analyse, design, and troubleshoot everything from a phone charger to a national power grid.

---

## 2  Ohm’s Law

**Statement.** For a metallic conductor at constant temperature, the current $I$ through it is **directly proportional** to the potential difference $V$ across it and **inversely proportional** to its resistance $R$:
$\boxed{\;V = I R\;}$

| Symbol | Quantity             | SI unit    |
| ------ | -------------------- | ---------- |
| $V$    | Potential difference | volt (V)   |
| $I$    | Current              | ampere (A) |
| $R$    | Resistance           | ohm (Ω)    |

### 2.1  Quick Example (MCQ slide)

*Problem.* A resistor has $R = 10\,Ω$ and the voltage across it is $V = 20\,V$. What is the current?
*Solution.* $I = V/R = 20\,\text{V} / 10\,Ω = \boxed{2\,\text{A}}$.  *(Option “2 A” is correct.)*

---

## 3  Circuit Topology Vocabulary

| Term       | Meaning                                                       |
| ---------- | ------------------------------------------------------------- |
| **Node**   | A point where two or more circuit elements meet.              |
| **Branch** | A single path between two nodes containing a circuit element. |
| **Loop**   | Any closed conducting path within a circuit.                  |

Why we care: Kirchhoff’s laws are written in terms of currents at **nodes** (KCL) and voltages around **loops** (KVL).

---

## 4  Kirchhoff’s Laws

### 4.1  Kirchhoff’s Current Law (KCL)

> **Charge conservation.** The algebraic sum of currents entering a node equals the sum leaving that node:
> $\sum I = 0$

*Traffic analogy:* what flows in must flow out — no charge pile‑up at a junction.

### 4.2  Kirchhoff’s Voltage Law (KVL)

> **Energy conservation.** The algebraic sum of voltage rises and drops around any closed loop is zero:
> $\sum V = 0$

Think of a hiker returning to the same altitude after a round‑trip: net height change = 0.

---

## 5  Worked Examples

### 5.1  KCL Node Example

Suppose three conductors meet at a node with $I_1 = 10\,\text{A}$ entering and $I_3 = 3\,\text{A}$ leaving. Find the third current $I_2$ (leaving):

$$
+I_1 - I_2 - I_3 = 0 \;\Rightarrow\; I_2 = I_1 - I_3 = 10\,A - 3\,A = \boxed{7\,A}.
$$

### 5.2  KVL Loop Example (slide “Solved Examples”)

*Circuit sketch:* One loop containing (in travel order)

1. 20 V battery (rise)
2. 10 Ω resistor (drop = $10I$)
3. 10 V source (drop)
4. 2 Ω resistor (drop = $2I$)
5. 40 V battery (drop)
6. 6 Ω resistor (drop = $6I$).

KVL equation (clockwise):

$$
+20\;\text{V} \; -10I +10\;\text{V} \; -2I \; -40\;\text{V} \; -6I = 0.
$$

Combine constants and $I$-terms:

$$-10 ; -18I = 0 \quad\Longrightarrow\quad I = -\frac{10}{18} = -0.556,\text{A}.
$$

**Interpretation.** The negative sign means the actual current flows opposite to the direction we assumed when writing the equation.

### 5.3  Sanity‑Check Tip

After solving, trace the loop again: voltage rises minus drops should now cancel to \~0 V. If not, revisit sign conventions.

---

## 6  Key Takeaways (Week 2)

* Memorise $V = IR$ and be fluent converting metric prefixes (mA, µA, kΩ, MΩ).
* Always label assumed current directions *before* applying KCL or KVL — the math will reveal if a direction was guessed wrong.
* Nodes → currents, loops → voltages. Keep them conceptually separate to avoid sign errors.

> *Practice every day*: Solve two quick Ohm/KCL/KVL problems to lock in the habits.