## 🧠 Overview

**Week 3** introduces the logic of **random sampling** and explains how sample statistics—such as the sample mean—follow their probability distributions. These ideas underpin all inferential statistics because they tell us *how much* a sample can be expected to vary from one draw to the next.

---

## 🎯 Learning Objectives

By the end of this lesson, you should be able to:

1. **Define** random sampling and explain why it matters.
2. **Distinguish** sampling *with* vs. *without* replacement.
3. **Apply and compare** four probability‑based sampling designs (simple, systematic, stratified, cluster).
4. **Explain** the concept of a *sampling distribution* and compute a **standard error**.
5. **Use** the **Central Limit Theorem (CLT)** to approximate probabilities for sample means.

---

## 1. Why Random Sampling?

Random sampling gives every population member a *known, non‑zero* chance of selection. This prevents hidden biases and lets us quantify sampling uncertainty with probability theory.

### 1.1 Sampling Frame

Before drawing a sample, assemble a **sampling frame**—a complete list of population units (e.g., a roster of students).

### 1.2 With vs. Without Replacement

| Style                   | Independence?                             | Same unit can appear twice? | Example                                                                       |
| ----------------------- | ----------------------------------------- | --------------------------- | ----------------------------------------------------------------------------- |
| **With Replacement**    | Yes                                       | Yes                         | Drawing numbered balls from a bag and putting each back before the next draw. |
| **Without Replacement** | No (probabilities change after each draw) | No                          | Lottery where each ticket is removed once it wins.                            |

---

## 2. Core Probability Sampling Designs

### 2.1 Simple Random Sampling (SRS)

* **How:** Every combination of *n* units is equally likely.
* **Selection probability:** *n / N* for each unit.
* **When useful:** Homogeneous populations, small to moderate N.

### 2.2 Systematic Sampling

* **How:** Choose a random start between 1 and *k*, then take every *k*‑th unit (where *k = N / n*).
* **Pros:** Easy to implement in the field.
* **Caution:** Avoid if the population list has hidden periodicity.

### 2.3 Stratified Sampling

* **How:** Divide the population into **strata** that are internally similar. Draw an SRS within each stratum (proportionally or with oversampling).
* **Benefit:** Improves precision when strata differ strongly (e.g., age groups in a health survey).

### 2.4 Cluster Sampling

* **How:** Break the population into naturally occurring **clusters** (e.g., classrooms). Randomly select clusters, then survey *all* units within each selected cluster.
* **Benefit:** Reduces travel/field costs.
* **Trade‑off:** Larger sampling error unless clusters are internally diverse.

---

## 3. Sampling Distribution of the Sample Mean

Given a population with mean **μ** and standard deviation **σ**:

* The **sample mean** $\bar{X}$ from an SRS of size *n* is itself a random variable.
* **Expected value:** $E[\bar{X}] = μ$
  ($\bar{X}$ is an *unbiased* estimator.)
* **Standard error (SE):**  $SE(\bar{X}) = \dfrac{σ}{\sqrt{n}}$
  (smaller SE → more precise estimates).

> **Finite‑population correction:** If sampling without replacement and the sample is a large fraction of N, multiply SE by $\sqrt{1 − n/N}$.

---

## 4. Central Limit Theorem (CLT)

Regardless of the population’s shape, the distribution of $\bar{X}$ approaches a **Normal** distribution as *n* becomes large (≈ 30+ for mild skew, larger for heavy skew).

### 4.1 Practical Rule

* Convert $\bar{X}$ to a *Z*‑score:
  $Z = \frac{\bar{X} − μ}{SE(\bar{X})}$
* Use the standard Normal table to find probabilities or critical values.

### 4.2 Quick Example

Population: μ = 60, σ = 10, sample size n = 36.
Probability that the sample mean is **below 62**:

1. SE = 10 / √36 = 1.667.
2. Z = (62 − 60) / 1.667 ≈ 1.20.
3. P(Z < 1.20) ≈ 0.884 (88.4 %).

---

## 5. Worked Practice Problems

1. **SRS Probability**
   N = 1 000, n = 100.
   a) P(unit selected) = 0.10.
   b) P(unit *not* selected) = 0.90.
2. **Systematic Sampling Indexing**
   N = 300, n = 20 ⇒ k = 15.
   Random start = 7 ⇒ sample indices = 7, 22, 37, …
3. **Standard Error & CLT**
   μ = 50, σ = 8, n = 64 → SE = 1.
   P($\bar{X} > 52$) ⇒ Z = 2 ⇒ P ≈ 0.0228.
4. **Without‑Replacement Draw**
   Bag: 5 red, 3 blue, 2 green.
   P(blue on second draw | no replacement) = (3/10)·(7/9) + (7/10)·(3/9) = 0.233.

---

## 6. Reflection Questions

* **Design Choice:** When would *cluster* sampling be preferable even if it increases variance?
* **Precision:** How does doubling n affect SE? *(Hint: SE halves.)*
* **CLT Limits:** What population features (e.g., heavy tails) slow the convergence to Normality?

---

**Next Steps:** Use a statistical package (R/Python) to simulate thousands of SRS draws from a non‑Normal population. Plot the resulting distribution of $\bar{X}$ and watch the bell curve emerge!
