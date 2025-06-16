## 📌 Cluster Sampling

> **Definition:** Cluster sampling breaks the population into **groups (clusters)**—often based on geography or natural groupings—then **randomly selects entire clusters**. Every unit in each chosen cluster is included in the sample.

---

### 1  Why Use Cluster Sampling?

* **Cost & logistics:** Reduces travel when units are widely dispersed.
* **Operational ease:** Easier field management (one cluster = one visit).
* **Useful frames:** Often easier to build a list of clusters than of all units.

---

### 2  How to Do It

1. **Define clusters:** e.g., schools, city blocks, households in an enumeration area.
2. **List all clusters** (the cluster frame).
3. **Select clusters at random** (often SRS of clusters).
4. **Survey every unit** within each selected cluster (one‐stage design).

> **Note:** Two‑stage designs sample *within* selected clusters to lower costs further, but we focus on the one‑stage example shown in the slide.

---

### 3  Slide Example (Worked)

> Population: 80 households, grouped into 4 clusters of 20.
> Task: Select 2 clusters at random and survey **all** households in them.

* **Overall sample size:** $n = 2 \text{clusters} × 20 \text{households} = 40.$
* **Probability a household is selected:**
  Only if its cluster is chosen: $P = 2/4 = 0.5 \;(50 %).

---

### 4  Pros & Cons

| Pros                                                                                  | Cons                                                                                     |
| ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Big cost/time savings when clusters are geographically compact.                       | Higher sampling error if units inside a cluster are similar (intra‑cluster correlation). |
| Practical when a complete population frame is unavailable but a cluster frame exists. | Unequal cluster sizes complicate weighting.                                              |

---

## 🔄 Cluster vs. Stratified Sampling

| Feature                             | **Cluster Sampling**                                                  | **Stratified Sampling**                                           |
| ----------------------------------- | --------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **Primary goal**                    | Reduce cost/logistics.                                                | Increase statistical precision & ensure subgroup coverage.        |
| **How groups are formed**           | Clusters should be **mini‑populations** (internally heterogeneous).   | Strata are **homogeneous** internally, different from each other. |
| **Selection stage**                 | Randomly pick **clusters**, then keep all (or some) units inside.     | Sample **within every stratum**—none are skipped.                 |
| **Representation of all subgroups** | Only selected clusters are represented.                               | Every stratum is represented by design.                           |
| **Effect on variance**              | Generally **increases** variance because of intra‑cluster similarity. | Generally **decreases** variance when strata means differ.        |
| **Best when**                       | Travel dominates cost; cluster listing easier than unit listing.      | Reliable stratum info exists and within‑stratum variance is low.  |

---

*Standalone reference for Week 3 – Cluster Sampling and its contrast with Stratified Sampling.*
