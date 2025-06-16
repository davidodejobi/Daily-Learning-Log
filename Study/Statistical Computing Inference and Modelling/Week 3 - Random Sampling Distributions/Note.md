## 📙 Week 3 Master Note

*Random Sampling, Key Sampling Concepts, and Distribution of Sample Statistics*

This master note merges:

1. **Concept Slides** (Population, Sample, Sampling Frame).
2. **Narrative Guide** (definitions, designs, CLT).
3. **Detailed Calculation Bank** (step‑by‑step arithmetic).

---

## 🧠 Overview

Random sampling is the backbone of statistical inference—providing representative subsets so that sample statistics faithfully mirror the population. This week unpacks **core sampling terminology**, **probability‑based designs**, and the **behavior of sample means** via the **Central Limit Theorem (CLT)**.

---

## 🎯 Learning Objectives

1. Define **population**, **sampling frame**, **sample**, and **sampling distribution**.
2. Distinguish *with* vs. *without* replacement sampling.
3. Apply SRS, systematic, stratified, and cluster designs; compute selection probabilities.
4. Derive the **standard error** of the sample mean and adjust with the **finite‑population correction**.
5. Use the CLT to convert sample‑mean questions into **Normal** probability problems.
6. Work through numerical examples that cement each idea.

---

## 1  Key Concepts in Sampling

| Term               | Plain Definition                                    | Visual Analogy        |
| ------------------ | --------------------------------------------------- | --------------------- |
| **Population**     | Entire collection of units of interest.             | Whole cake.           |
| **Sampling Frame** | The *list* of population units that can be sampled. | Bakery’s order sheet. |
| **Sample**         | Subset actually selected for measurement.           | A slice of cake.      |

> **Frame ≠ Population?** If units are missing from the frame, they can’t be chosen → **coverage bias**.

#### Illustrative Example: Population vs. Sampling Frame

| Concept            | Concrete Example                                                              | Included Units                                                                                                              | Missing Units                                                                                                                                   |
| ------------------ | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Population**     | **All households in Lagos State** as of 1 Jan 2026 (≈ 5 million dwellings).   | Every dwelling—urban apartments, rural huts, staff quarters, informal settlements, even newly built but unregistered homes. | None—by definition it is the full target set.                                                                                                   |
| **Sampling Frame** | Latest **utility‑customer database** (addresses receiving electricity bills). | Dwellings connected to the power grid and officially recorded by the utility company.                                       | Off‑grid homes, vacant buildings, informal‑settlement shacks without official meters, newly constructed houses not yet entered in the database. |

*Take‑away:* The sampling frame is the practical list we sample from. Any population units missing from that list create **coverage error**, potentially biasing results if the omitted units differ systematically from those listed.

### 1.1  Sampling With vs. Without Replacement

| Style               | Independence? | Can a unit be selected twice? |
| ------------------- | ------------- | ----------------------------- |
| With replacement    | Yes           | Yes                           |
| Without replacement | No            | No                            |

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
