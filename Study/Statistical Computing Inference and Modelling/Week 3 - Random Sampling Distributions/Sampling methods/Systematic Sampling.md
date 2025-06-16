## 📌 Systematic Sampling

> **Definition:** Systematic sampling selects every *k*-th unit from an ordered list after a **random start**. The fixed interval *k* is calculated as *k = N / n*, where *N* is population size and *n* is desired sample size.

---

### 1  Why Use Systematic Sampling?

* **Field simplicity:** Once *k* is set, selection is quick—ideal for large, ordered lists.
* **Even spread:** Produces a sample evenly distributed across the frame.
* **Lower cost:** Fewer random numbers to generate than SRS.

---

### 2  How to Do It

1. **List the population** in any convenient order (spreadsheet, roster, etc.).
2. **Compute the interval:** *k = N / n* (round as needed).
3. **Choose a random start** *r* between 1 and *k* (using RNG or a random-number table).
4. **Select units:** *r, r + k, r + 2k, …* until *n* units are chosen.

> **Tip:** Keep the list order unchanged once the start is chosen to avoid bias.

---

### 3  Slide Example (Worked)

> Population: 500 students.
> Desired sample: 50 students.

1. **Interval:** *k = 500 / 50 = 10*.
2. **Random start:** Suppose *r = 6* (randomly picked 1–10).
3. **Sample indices:** 6, 16, 26, 36, … , 496.

* **Selection probability for any student:** 1 / 10 = 0.10 (10 %).

---

### 4  Choosing the Random Start

* Generate a random integer **uniformly** between 1 and *k*.
* Ensures every possible systematic sample has equal probability.

---

### 5  Pros & Cons

| Pros                                       | Cons                                                                     |
| ------------------------------------------ | ------------------------------------------------------------------------ |
| Easy and fast in the field.                | Hidden periodic patterns in the list can bias the sample.                |
| Provides uniform coverage across the list. | Requires complete ordered list upfront.                                  |
| Fewer random numbers than SRS.             | Selection probability fixed, so unequal probabilities hard to implement. |

---

### 6  Quick Check Exercise

Population of 1 200 items, need sample of 80.

1. Find *k.*
2. If random start = 4, list first five selected indices.

*(Answers: k = 15; indices 4, 19, 34, 49, 64.)*

---

*Standalone reference for Week 3 – Systematic Sampling.*
