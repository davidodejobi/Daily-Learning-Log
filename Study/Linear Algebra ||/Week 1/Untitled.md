# MIVA – MTH 204

## Week 1 Study Notes

---

### Lesson Objectives

* Identify what makes an equation **linear**.
* Define a **system** of linear equations.
* List the three **elementary row operations**.
* Solve systems with the **Gaussian‑elimination** technique.

---

## 1  Linear equations & their systems

A **linear equation** in variables $x_1,x_2,\dots ,x_n$ can be written

$$
 a_1x_1+a_2x_2+\dots +a_nx_n=b,
$$

where the coefficients $a_i$ and the constant $b$ are real (or complex) numbers.

A **system of linear equations** is a collection of two or more linear equations sharing the same variables.

| Term             | Meaning                                                                       |
| ---------------- | ----------------------------------------------------------------------------- |
| **Consistent**   | At least one solution exists.                                                 |
| **Inconsistent** | No solution exists.                                                           |
| **Independent**  | Exactly one solution (the lines/planes intersect at a single point).          |
| **Dependent**    | Infinitely many solutions (the equations describe the same geometric object). |

---

## 2  Matrix representation

1. **Coefficient matrix** $A$ – the numbers $a_{ij}$ alone.
2. **Augmented matrix** $[A\,|\,b]$ – the coefficient matrix with the constants column appended.

Writing the system in matrix form $A\mathbf x=\mathbf b$ lets us manipulate rows mechanically.

---

## 3  Elementary row operations

Gaussian elimination relies on three moves that keep the solution set unchanged:

1. **Row swap** $R_i\leftrightarrow R_j$
2. **Scaling a row** $kR_i\to R_i$ (with $k\neq0$)
3. **Row replacement** $R_i+kR_j\to R_i$

---

## 4  Gaussian elimination – overview

> The method consists of two parts: forward elimination and back substitution.

### 4.1 Forward elimination

Transform the augmented matrix to **row‑echelon form (REF)**:

* All non‑zero rows lie above any all‑zero rows.
* The *leading 1* (pivot) of each non‑zero row appears to the right of the leading 1 in the row above.

If a contradictory row such as $[0\,0\,0\,|\,c]\ (c\neq0)$ appears, the system is **inconsistent**.

### 4.2 Backward substitution

Once in REF (or the stricter reduced REF), solve for the last pivot variable and substitute upward to obtain all unknowns.

---

## 5  Step‑by‑step algorithm

1. **Locate** the left‑most non‑zero column; swap rows to bring a non‑zero entry to the top.
2. **Scale** that row to make the pivot 1.
3. **Zero‑out all entries below** the pivot using row replacement.
4. **Cover** the row just used and **repeat** the process on the sub‑matrix that remains (moving down and right).
5. When the last pivot is placed, **work upward**: scale pivots (if necessary) and eliminate the entries *above* each pivot to reach reduced REF.

---

## 6  Worked example (3 × 3)

Original system

$$
\begin{aligned}
 x_1-3x_2-2x_3 &= 6\\
 2x_2+x_3 &= -4\\
 -3x_2+2x_3 &= 13
\end{aligned}
$$

| Step | Operation                                                    | Augmented matrix          |           |                          |                   |
| ---- | ------------------------------------------------------------ | ------------------------- | --------- | ------------------------ | ----------------- |
| 1    | $R_2\leftarrow -2R_1+R_2$                                    | (\begin{bmatrix}1&-3&-2&  | &6\0&5&5& | &-16\\-3&6&8&            | &-5\end{bmatrix}) |
| 2    | $R_3\leftarrow 3R_1+R_3$                                     | (\begin{bmatrix}1&-3&-2&  | &6\0&5&5& | &-16\0&-3&2&             | &13\end{bmatrix}) |
| 3    | $R_2\leftarrow \tfrac{1}{5}R_2$                              | (\begin{bmatrix}1&-3&-2&  | &6\0&1&1& | &-\tfrac{16}{5}\0&-3&2&  | &13\end{bmatrix}) |
| 4    | $R_1\leftarrow R_1+3R_2;\; R_3\leftarrow R_3+3R_2$           | (\begin{bmatrix}1&0&-1/2& | &0\0&1&1& | &-\tfrac{16}{5}\0&0&7/2& | &7\end{bmatrix})  |
| 5    | $R_3\leftarrow \tfrac{2}{7}R_3$                              | (\begin{bmatrix}1&0&-1/2& | &0\0&1&1& | &-\tfrac{16}{5}\0&0&1&   | &2\end{bmatrix})  |
| 6    | $R_1\leftarrow R_1+\tfrac{1}{2}R_3;\; R_2\leftarrow R_2-R_3$ | (\begin{bmatrix}1&0&0&    | &1\0&1&0& | &-3\0&0&1&               | &2\end{bmatrix})  |

Solution: $x_1=1,\;x_2=-3,\;x_3=2$.

---

## 7  Why Gaussian elimination matters

* **Universality** – works on any finite linear system.
* **Foundation for advanced topics** – LU‑decomposition, determinants, rank, eigen‑analysis, and numerical linear algebra all build on REF ideas.
* **Algorithmic efficiency** – straightforward to implement on a computer; forms the core of most linear‑solver libraries.

---

## 8  Quick self‑check

1. List the three elementary row operations.
2. Explain how you detect an inconsistent system during elimination.
3. Carry out forward elimination on
   $\begin{aligned}x+2y+z&=2\\2x+5y+z&=5\\-x+4y+2z&=6\end{aligned}$
   and state its REF.

---

## 9  Further reading

* Lay, D. C. *Linear Algebra and Its Applications* (5th ed.)
* Carrell, J. B. *Fundamentals of Linear Algebra*
* Lipschutz & Lipson. *Schaum’s Outline of Linear Algebra*

---

### Key takeaway

Mastering **Gaussian elimination** equips you with a systematic toolbox for solving any linear system—from hand‑worked homework to large‑scale computational models.
