## 📌 Sampling Distribution of the Mean & Central Limit Theorem (CLT)

### 1  What Is a Sampling Distribution?

* **Definition:** The probability distribution of a statistic—here, the **sample mean** $\bar{X}$—over **all possible SRS samples** of a fixed size *n* from the population.
* **Key facts for the sample mean** (when sampling without replacement but *n/N* is small):
  • Center: $E[\bar{X}] = μ$ (unbiased).
  • Spread: **Standard error** $SE(\bar{X}) = σ/\sqrt{n}$ (or ×√(1−n/N) for large fractions).

---

### 2  Central Limit Theorem (CLT)

> **Statement:** For sufficiently large *n* (≈ 30+ for mild skew populations), the standardized sample mean

$$
Z = \frac{\bar{X} - μ}{SE(\bar{X})}
$$

**approximates** the standard Normal distribution $N(0,1).$

**Why it matters:** Lets us use the Normal table to find probabilities or build confidence intervals—even when the original data are not Normal.

---

### 3  Worked Slide Example

> **Population:** Normal with μ = 60, σ = 10.
> **Sample size:** *n* = 36.
> **Question:** $P(\bar{X} < 62)$

**Step‑by‑step:**

1. **Compute SE:**
   $SE = \frac{σ}{\sqrt{n}} = \frac{10}{\sqrt{36}} = 1.667.$
2. **Convert to Z‑score:**
   $Z = \frac{62 − 60}{1.667} ≈ 1.20.$
3. **Lookup in Z‑table:**
   $P(Z < 1.20) ≈ 0.884.$

> **Interpretation:** A random sample of 36 will have a mean below **62** about **88 %** of the time.

---

### 4  Quick Reminders

* **SE vs σ:** SE shrinks with √n, reflecting more precise means from larger samples.
* **Finite‑Population Correction (fpc):** If *n/N* > 0.05, adjust SE: $SE × √(1−n/N).$
* **Skewed Populations:** Need larger *n* for CLT to give a good Normal approximation.

---

### 5  Mini‑Practice

1. Population μ = 50, σ = 12, sample n = 25.
   a) Compute SE.
   b) Find $P(\bar{X} > 55).$
2. Why does quadrupling *n* cut SE in half? Show algebraically.

*Standalone reference for Week 3 – Sampling Distribution & CLT.*
