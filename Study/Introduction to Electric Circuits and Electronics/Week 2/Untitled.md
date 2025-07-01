# Worksheet Solutions – Ohm’s & Kirchhoff’s Laws

These worked answers match every question in the “Ohm’s and Kirchhoff’s Laws” worksheet fileciteturn4file0.

---

## 1  Ohm’s‑Law Calculations

> *Formulae:* $V = I R, \; I = V / R, \; R = V / I$.  Always convert to **base SI units** (amps, volts, ohms) before solving, then reconvert to a convenient metric prefix.

| #  | Given (SI base)                                                                           | Unknown | Working                        | **Scientific notation**  | **Metric‑prefix answer** |
| -- | ----------------------------------------------------------------------------------------- | ------- | ------------------------------ | ------------------------ | ------------------------ |
| 1  | $I = 20\,\text{mA} = 0.020\,\text{A},\; R = 5\,\text{kΩ} = 5.0×10^{3}\,Ω$                 | V       | $V = 0.020×5.0×10^{3}$         | $1.0×10^{2}\,\text{V}$   | **100 V**                |
| 2  | $I = 150\,µA = 1.50×10^{-4}\,\text{A},\; R = 47\,\text{kΩ} = 4.7×10^{4}\,Ω$               | V       | $V = 1.50×10^{-4}×4.7×10^{4}$  | $7.05×10^{0}\,\text{V}$  | **7.05 V**               |
| 3  | $V = 24\,\text{V},\; R = 3.3\,\text{MΩ} = 3.3×10^{6}\,Ω$                                  | I       | $I = 24/3.3×10^{6}$            | $7.27×10^{-6}\,\text{A}$ | **7.27 µA**              |
| 4  | $V = 7.2\,\text{kV} = 7.2×10^{3}\,\text{V},\; R = 900\,Ω$                                 | I       | $I = 7.2×10^{3}/900$           | $8.00×10^{0}\,\text{A}$  | **8 A**                  |
| 5  | $V = 1.02\,\text{mV} = 1.02×10^{-3}\,\text{V},\; I = 40\,µA = 4.0×10^{-5}\,\text{A}$      | R       | $R = 1.02×10^{-3}/4.0×10^{-5}$ | $2.55×10^{1}\,Ω$         | **25.5 Ω**               |
| 6  | $V = 3.5\,\text{GV} = 3.5×10^{9}\,\text{V},\; I = 0.76\,\text{kA} = 7.6×10^{2}\,\text{A}$ | R       | $R = 3.5×10^{9}/7.6×10^{2}$    | $4.61×10^{6}\,Ω$         | **4.61 MΩ**              |
| 7  | $I = 0.00035\,\text{A},\; R = 5350\,Ω$                                                    | V       | $V = 0.00035×5350$             | $1.87×10^{0}\,\text{V}$  | **1.87 V**               |
| 8  | $I = 1.71×10^{6}\,\text{A},\; R = 0.002\,Ω$                                               | V       | $V = 1.71×10^{6}×0.002$        | $3.42×10^{3}\,\text{V}$  | **3.42 kV**              |
| 9  | $V = 477\,\text{V},\; R = 0.00500\,Ω$                                                     | I       | $I = 477/0.00500$              | $9.54×10^{4}\,\text{A}$  | **95.4 kA**              |
| 10 | $V = 0.02\,\text{V},\; R = 9.92×10^{5}\,Ω$                                                | I       | $I = 0.02/9.92×10^{5}$         | $2.02×10^{-8}\,\text{A}$ | **20.2 nA**              |
| 11 | $V = 1.50×10^{5}\,\text{V},\; I = 233\,\text{A}$                                          | R       | $R = 1.50×10^{5}/233$          | $6.44×10^{2}\,Ω$         | **644 Ω**                |
| 12 | $V = 8.4×10^{-6}\,\text{V},\; I = 0.011\,\text{A}$                                        | R       | $R = 8.4×10^{-6}/0.011$        | $7.64×10^{-4}\,Ω$        | **0.764 mΩ**             |

---

## 2  Parallel‑Branches Circuit (1.5 V | 100 Ω | 9 V + 200 Ω)

**Assumptions (shown on lecture slide):**

* Common top node voltage = $V_N$.
* Bottom node is reference (0 V).
* Batteries are *ideal* (no explicit internal resistance) – this means the top node is **forced to 1.5 V** by the 1.5 V source; the 9 V source then drives current *into* the node via its 200 Ω series resistor.
* Currents **downward** are taken positive.

| Branch         | Current expression        | Numerical value                                     |
| -------------- | ------------------------- | --------------------------------------------------- |
| 1.5 V battery  | $I_{1.5} = ?$             | determined by KCL                                   |
| 100 Ω resistor | $I_{100} = V_N/100$       | $1.5/100 = 0.015\,\text{A}$ ↓                       |
| 9 V + 200 Ω    | $I_{200} = (V_N - 9)/200$ | $(1.5-9)/200 = -0.0375\,\text{A}$ (‑ve = 37.5 mA ↑) |

### Apply KCL at the node (downward +)

$I_{1.5} + 0.015\,A - 0.0375\,A = 0 \;\Rightarrow\; I_{1.5} = 0.0225\,\text{A}.$

So **22.5 mA flows *down* through the 1.5 V battery** (battery is being charged).

### Power dissipations

| Element        | Current   | Power $P = I^2R$                   |
| -------------- | --------- | ---------------------------------- |
| 100 Ω resistor | 15.0 mA ↓ | $0.015^2 × 100 ≈ 0.0225\,\text{W}$ |
| 200 Ω resistor | 37.5 mA ↑ | $0.0375^2 × 200 ≈ 0.281\,\text{W}$ |

> *Check:* Node‑voltage method yields the same currents; the algebraic sum of branch currents is zero, satisfying KCL.

---

## 3  Unknown‑Battery Series Circuit (4 Ω & R)

The worksheet references a second diagram, but the PDF text doesn’t list the actual component values apart from “4 Ω resistor” and “battery on the right”.

⚠️ **Please upload (or describe) the full schematic** so that we can compute:

1. The battery voltage $V$ on the right,
2. The current through the 4 Ω resistor,
3. The resistance of the unknown resistor $R$.

Once the diagram (or its numeric details) is available, I’ll add a complete step‑by‑step solution here.

---

### Key Takeaways

* Always normalise prefixes before using Ohm’s Law; it avoids calculator slips.
* In parallel‑source puzzles, picking a reference node and writing KCL is the quickest path.
* Real batteries have internal resistance; ideal unequal sources in parallel are strictly non‑physical, but treating one node as fixed lets beginners practise KCL/KVL.

---

*(End of solutions v1 — awaiting the second‑circuit schematic for final answers.)*

