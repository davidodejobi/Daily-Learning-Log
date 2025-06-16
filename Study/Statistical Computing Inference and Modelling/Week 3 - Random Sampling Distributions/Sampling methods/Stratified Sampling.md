## 📌 Stratified Sampling

> **Definition:** Stratified sampling divides the population into **non‑overlapping subgroups**—called **strata**—that are internally homogeneous with respect to the study variable. An SRS (or other design) is then performed **within each stratum**. This guarantees representation of every stratum and can dramatically reduce sampling variance when strata differ in their means.

---

### 1  Why Use Stratification?

* **Precision gain:** If strata means differ but within‑stratum variance is low, the overall estimator variance can be **much smaller** than a single SRS of the same total size.
* **Guaranteed subgroup coverage:** Ensures small but important groups (e.g., minority regions) are sampled.
* **Operational convenience:** Different field teams can handle each stratum separately.

---

### 2  Design Variants

| Variant              | Allocation Rule                 | When to Use                                                               |
| -------------------- | ------------------------------- | ------------------------------------------------------------------------- |
| **Proportional**     | $n_i = n \times \tfrac{N_i}{N}$ | Default choice when cost per unit ≈ same everywhere.                      |
| **Equal (Uniform)**  | Same $n_i$ in each stratum      | When comparisons among strata are key; boosts precision for small strata. |
| **Optimal (Neyman)** | $n_i ∝ N_i σ_i$                 | Minimises variance when stratum SDs differ and cost per unit constant.    |

The **total sample size** is $n = \sum_{i=1}^H n_i$ where *H* = number of strata.

---

### 3  Implementation Steps

1. **Define strata:** Choose variables strongly related to the target outcome (e.g., age group, geographic region).
2. **Construct frames:** Build a sampling frame for each stratum separately.
3. **Decide allocation:** proportional, equal, or Neyman.
4. **Draw samples:** Usually SRS within each stratum; store selected IDs plus their stratum labels.
5. **Weighting:** Initial weight of unit $k$ in stratum $i$ = $w_{ik} = \tfrac{N_i}{n_i}$.

---

### 4  Selection Probability & Inclusion

For any specific unit in stratum $i$:

$$
P(\text{selected}) = \frac{n_i}{N_i}.
$$

The overall probability differs by stratum when allocations are non‑proportional.

---

### 5  Worked Example (Slide Scenario)

> **Population:** *N* = 120 individuals split into **3 strata** of 40.
> **Sample:** Select **10** individuals per stratum (equal allocation).

1. **Overall sample size:**

   $$
     n = n_1 + n_2 + n_3 = 10 + 10 + 10 = 30.
   $$
2. **Probability a unit in stratum 1 is selected:**

   $$
     P_1 = \frac{n_1}{N_1} = \frac{10}{40} = 0.25\;\text{(25 %)}.
   $$
3. **Weight for estimation:** Each sampled unit in any stratum represents $w = 40/10 = 4$ population units.

---

### 6  Estimator Properties

| Statistic              | Weighted Formula                                                 | Variance                                                           |
| ---------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Overall mean**       | $\bar{X}_{str} = \sum_{i=1}^H W_i \bar{X}_i$ where $W_i = N_i/N$ | Var = $\sum W_i^2 \frac{σ_i^2}{n_i}\left(1−\frac{n_i}{N_i}\right)$ |
| **Overall proportion** | $\hat{p}_{str} = \sum W_i \hat{p}_i$                             | Replace $σ_i^2$ with $p_i(1−p_i)$                                  |

> **Key:** Variance drops when within‑stratum variances $σ_i^2$ are small.

---

### 7  Strengths & Limitations

| Strengths                                     | Limitations                                          |
| --------------------------------------------- | ---------------------------------------------------- |
| Improves precision without larger *n*.        | Requires **stratum info** in advance.                |
| Guarantees representation of minority groups. | More complex weighting & variance formulas.          |
| Allows separate estimates per stratum.        | Potentially costly if some strata are hard to reach. |

---

### 8  Practical Tips

* **Homogeneity rule:** Create strata that are homogeneous **within** and heterogeneous **between**.
* **Minimum $n_i$:** Even with proportional allocation ensure each stratum gets enough units for variance estimation (e.g., $n_i ≥ 5$).
* **Weight check:** After data collection, adjust for non‑response by inflating weights within each stratum.

---

### 9  Mini‑Exercises

1. **Proportional Allocation:** Population: $N_1=50, N_2=150, N_3=300$. Total sample $n=100$. Find $n_i$.  *(Ans: 10, 30, 60)*
2. **Selection Probability:** With $n_i = \{10,30,60\}$ above, compute $P_i$ for each stratum.
3. **Variance Gain:** Compare variance of $\bar{X}$ under stratified (proportional) vs. SRS for a scenario where $σ_1=2, σ_2=8, σ_3=10$.

---

*Prepared as a standalone reference for Week 3 – Stratified Sampling.*
