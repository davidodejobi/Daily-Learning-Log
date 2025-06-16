## 📌 Simple Random Sampling (SRS)

> **Definition:** A sampling method where **every possible subset** of size *n* from a population of size *N* has the **same chance** of being chosen. Therefore, each individual’s selection probability is *n / N*.

---

### 1  Why Use SRS?

* **Baseline design:** Foundation for many theoretical results (unbiased mean, easy variance).
* **Eliminates selection bias:** Works if a complete sampling frame exists.
* **Straightforward math:** Simplest standard‑error formulas.

---

### 2  How to Do It

1. **Number** every unit 1 … *N* (sampling frame).
2. **Decide** sample size *n*.
3. **Randomly pick** *n* distinct numbers (random‑number table or computer RNG).
4. **Survey** all selected units—no substitutions.

---

### 3  Selection Probability

* **Any individual:**
  $P(\text{selected}) = \tfrac{n}{N}.$
* **Any specific set of *n* units:**
  $P(\text{that set}) = \frac{1}{\binom{N}{n}}.$

---

### 4  Quick Example

Population *N* = 100, sample *n* = 15.
Probability an individual (ID #23) is in the sample: 15/100 = 0.15 (15 %).

---

### 5  Estimator Snapshot (Without‑Replacement Variance)

| Statistic             | Expected Value | Variance                                      |
| --------------------- | -------------- | --------------------------------------------- |
| Mean ($\bar X$)       | μ              | $\dfrac{σ^2}{n}\Bigl(1−\tfrac{n}{N}\Bigr)$    |
| Proportion ($\hat p$) | p              | $\dfrac{p(1−p)}{n}\Bigl(1−\tfrac{n}{N}\Bigr)$ |

> **Finite‑population correction (fpc)** $(1−n/N)$ becomes important if *n/N* > 0.05.

---

### 6  Pros & Cons

| Pros                                    | Cons                                                 |
| --------------------------------------- | ---------------------------------------------------- |
| Easy to analyse; unbiased estimators.   | Requires complete frame.                             |
| Simple variance formulas.               | Can be costly if sampled units are widely scattered. |
| Serves as baseline for complex designs. | Does not guarantee subgroup representation.          |

---

### 7  Mini‑Checks

1. Class of 45, sample 9: P(not selected) = 0.8.
2. If σ = 12, N = 500, n = 50 → SE($\bar X$) = 12 / √50 × √(1−0.1) ≈ 1.51.

---

*Trimmed reference for Week 3 – Simple Random Sampling*
