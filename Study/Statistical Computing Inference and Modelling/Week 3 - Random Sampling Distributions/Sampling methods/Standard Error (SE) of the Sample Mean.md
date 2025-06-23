## 📌 Standard Error (SE) of the Sample Mean

> **Definition:** The **standard error** quantifies how much the sample mean $\bar{X}$ is expected to vary from sample to sample due **only to random sampling**.

---

### 1  Formula

For an SRS of size *n* drawn from a population with standard deviation **σ**:

$$
SE(\bar{X}) = \frac{σ}{\sqrt{n}}.
$$

* **σ** — population standard deviation (or the sample SD *s* if σ is unknown).
* **n** — sample size.

> **Interpretation:** Larger samples (bigger *n*) shrink the denominator’s √n, making SE smaller—so estimates are more precise.

---

### 2  Why SE Matters

* **Confidence intervals:** Margin of error = *z<sub>α/2</sub>* × SE.
* **Hypothesis tests:** Test statistic = (estimate − hypothesised value) / SE.
* **CLT connection:** SE is the scaling factor that turns $\bar{X}$ into a Normal *z*-score for large *n*.

---

### 3  Quick Example

Population σ = 10, sample n = 25.

$$
SE = \frac{10}{\sqrt{25}} = 2.
$$

If $\bar{X} = 62$ and μ = 60:

$$
Z = \frac{62 − 60}{2} = 1.
$$

Table gives P(Z > 1) ≈ 0.159.

#### Full Example – Standard Error & CLT

**Question (verbatim from slide):**

> *“Assume a population with a **non‑normal distribution**, where the mean (μ) is 50, and the standard deviation (σ) is 15. If you take a random sample of 100 individuals from this population, use the **Central Limit Theorem** to approximate the probability that the sample mean is less than 52 **and** calculate the standard error of the sample mean.”*

---

**Given values**

* Population mean (μ): **50**
* Population standard deviation (σ): **15**
* Sample size (n): **100**
* Threshold value for sample mean: **52**

#### Step‑by‑Step Solution‑by‑Step Solution

| Step                                          | Work                                                           | Result    |
| --------------------------------------------- | -------------------------------------------------------------- | --------- |
| **1. Compute the Standard Error (SE)**        | $SE(\bar X) = \dfrac{σ}{\sqrt{n}} = \dfrac{15}{\sqrt{100}}$    | **1.5**   |
| **2. Convert the boundary (52) to a Z‑score** | $Z = \dfrac{52 − μ}{SE} = \dfrac{52 − 50}{1.5}$                | **1.33**  |
| **3. Look up left‑tail probability**          | From the Z‑table, $P(Z \le 1.33) \approx 0.908$                | **0.908** |
| **4. State the interpretation**               | About **90.8 %** of samples of size 100 will have a mean < 52. | —         |

> **Key idea:** Even though the population is non‑Normal, the large sample size (100) lets us use the CLT to treat $\bar X$ as approximately Normal.

---

#### Quick Check

* If the bound were **55**, the Z‑score would be $(55−50)/1.5 = 3.33$ ⇒ left‑tail ≈ 0.9996 ⇒ $P(\bar X < 55)$ ≈ 0.9996, so $P(\bar X > 55)$ ≈ 0.0004.

*This document presents the full wording and a clear, four‑step calculation.*


---

### 4  Finite-Population Correction (fpc)

If sampling **without replacement** and *n/N* > 0.05,

$$
SE_{adj} = SE × \sqrt{1 − n/N}.
$$

---

### 5  Mini‑Checks

1. σ = 8, n = 64 → SE? *(Ans: 1)*
2. Double n from 25 to 50; how does SE change? *(SE ↓ by √2 ≈ 1.41× smaller)*

*Standalone reference – Standard Error of the Mean.*
