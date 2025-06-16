## 📌 Sampling *With* vs. *Without* Replacement

> **Key Idea:** After each draw, do you **return** the selected unit to the population (*with replacement*, WR) or **remove** it (*without replacement*, WOR)? This choice affects probabilities and independence between draws.

---

### 1  Definitions

| Mode                          | What Happens After a Draw                                | Independence Between Draws             | Same unit can be chosen twice? |
| ----------------------------- | -------------------------------------------------------- | -------------------------------------- | ------------------------------ |
| **With Replacement (WR)**     | Item is returned to the population before the next draw. | **Yes** (probabilities stay the same). | **Yes**                        |
| **Without Replacement (WOR)** | Item is **not** returned; it cannot appear again.        | **No** (probabilities change).         | **No**                         |

---

### 2  Probability Impact – Two Slide Examples

#### 2.1 Two Red Marbles (WOR)

Bag: 20 marbles (8 red, 12 blue). Draw 2 without replacement.

$$
P(\text{2 red}) = \tfrac{8}{20} \times \tfrac{7}{19} = 0.147.
$$

#### 2.2 Blue on 2nd Draw (WR)

Box: 10 balls (5 R, 3 B, 2 G). Replace after first draw.

Second draw is independent of first:

$$
P(\text{blue on 2nd}) = \tfrac{3}{10} = 0.30.
$$

*(Compare: if **no** replacement, probability depends on what came out first.)*

---

### 3  When to Use Each Mode

| Prefer **WR**                                                                                      | Prefer **WOR**                                                                    |
| -------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| The population is conceptually infinite (e.g., manufacturing line).                                | Sampling finite populations where duplication is impossible (people, households). |
| You need independent, identically distributed (i.i.d.) observations for certain statistical tests. | You wish to avoid picking the same item twice (lottery draws, audits).            |

---

### 4  Quick Check

Bag: 6 balls, colours all unique. Draw 2.

1. *WR* – P(draw the same ball twice)? → 1/6.
2. *WOR* – P(draw 2 specific balls in any order)? → 2/6 × 1/5 = 0.067.

---

*Standalone reference for Week 3 – Sampling With vs. Without Replacement*
