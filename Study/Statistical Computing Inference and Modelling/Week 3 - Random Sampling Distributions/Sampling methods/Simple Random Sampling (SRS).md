## 📌 Simple Random Sampling (SRS)

> **Definition:** SRS is a probability‑based technique in which **every possible subset** of size *n* from a population of size *N* has an **equal chance** of being selected. Consequently, each individual unit also has an identical selection probability of *n/N*.

---

### 1  Why use SRS?

* Provides a benchmark design—the basis for many theoretical results (e.g., unbiasedness of $\bar{X}$).
* Eliminates systematic selection bias when a complete sampling frame is available.
* Simplifies variance and standard‑error formulas.

---

### 2  Implementation Steps

1. **Create the sampling frame** (number each unit 1 … *N*).
2. **Choose sample size** *n* (based on precision goals and resources).
3. **Select units:**

   * *Random‑number table* or *computer RNG* to generate *n* distinct integers.
4. **Contact / measure** every selected unit—no substitutions.

> **Tip:** In software (R/Python), `sample(1:N, n, replace = FALSE)` performs SRS.

---

### 3  Selection Probability & Inclusion

For any **specific** unit:

$$
P(\text{selected}) = \frac{n}{N}.
$$

For **any** set of *n* distinct units (an “$n$-tuple”):

$$
P(\text{select that set}) = \frac{1}{\binom{N}{n}}.
$$

---

### 4  Worked Example

> **Scenario:** Population of *N* = 100 individuals. Draw *n* = 15 via SRS. What is the probability that a particular individual (e.g., ID #23) is included?

Solution:

P(#23 selected) = 15 / 100 = 0.15 (15 %)

---

### 5  Estimator Properties

| Statistic             | Formula                                    | Expected Value    | Variance (without replacement)                                    |
| --------------------- | ------------------------------------------ | ----------------- | ----------------------------------------------------------------- |
| **Sample mean**       | $\bar{X} = \tfrac{1}{n}\sum_{i=1}^{n} X_i$ | E\[$\bar{X}$] = μ | Var($\bar{X}$) = $\tfrac{\sigma^2}{n}\left(1−\tfrac{n}{N}\right)$ |
| **Sample proportion** | $\hat{p} = \tfrac{x}{n}$                   | E\[$\hat{p}$] = p | Var($\hat{p}$) = $\tfrac{p(1−p)}{n}\left(1−\tfrac{n}{N}\right)$   |

> The **finite‑population correction (fpc)** term $(1−n/N)$ matters once *n/N* > 0.05.

---

### 6  Strengths & Limitations

| Strengths                                                         | Limitations                                                                               |
| ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Easiest to analyse; unbiased estimators.                          | Requires *complete* frame—rare for hard‑to‑reach populations.                             |
| Straightforward standard‑error formulas.                          | Fieldwork cost can be high if sampled units are geographically dispersed.                 |
| Basis for other complex designs (post‑stratification, weighting). | No built‑in control over subgroup sizes (may under‑represent small but important strata). |

---

### 7  Practical Tips

* Use reproducible random seeds for audit trails.
* If sample units are people, anticipate non‑response—plan callbacks or replacements *before* starting.
* For very large *N*, consider **systematic SRS** (select every *k*‑th after a random start) to simplify selection while retaining SRS properties.

---

### 8  Mini‑Exercises

1. **Selection Probability**: In a class of 45 students, an SRS of 9 is taken. What is P(student *not* selected)? *(Ans: 0.8)*
2. **Estimator Variance**: Population σ = 12, N = 500, n = 50. Compute SE($\bar{X}$) with fpc.
3. **Simulation**: Write R/Python code to draw 10 000 SRS samples (*n* = 30) from a skewed population and plot the distribution of $\bar{X}$.

---

*Prepared as a standalone reference for Week 3 – Simple Random Sampling.*
