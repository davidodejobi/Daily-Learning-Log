# IFT 212 – Week 2 Addendum

## Data Representation & Binary Arithmetic

### 1 Kick‑off Quiz

> **What is the primary function of the Central Processing Unit (CPU)?**
> A. Store data  B. Process information  C. Control I/O devices  D. Power the computer

**Answer:** **B – Process information.** The CPU is the brain that *executes instructions* and processes data.

---

### 2 Why Binary?

Computers are built from electronic switches that are either **on** (1) or **off** (0); therefore, every piece of information—text, images, video, sound—is ultimately encoded as sequences of **zeros and ones** called **binary digits (bits)**.

* **Bit** – the smallest unit, representing 0 or 1.
* **Byte** – 8 bits; enough to encode a single text character under common schemes.

> Analogy: Think of binary as a secret two‑word language—“ha” and “na.” By stringing these two words in different orders, you can express any sentence. Likewise, computers string 0s and 1s to represent everything.

---

### 3 ASCII Example

**ASCII** (American Standard Code for Information Interchange) maps characters to numerical codes that hardware can handle.

| Character | Decimal Code | Binary (8‑bit) |
| --------- | ------------ | -------------- |
| **A**     | 65           | `01000001`     |

So the letter **A** stored in memory is literally the pattern `01000001`.

---

### 4 Binary Arithmetic – Adding 5 and 3

1. **Convert to binary**

   * 5 → `101`
   * 3 → `011`
2. **Align bits** (pad left with zeros):

```
  101   (5)
+ 011   (3)
------
```

3. **Add bit by bit** (right‑to‑left), carrying when sum ≥ 2:

```
  101
+ 011
------
 1000   (binary)
```

4. **Convert result back to decimal** → `1000₂` = **8₁₀**.

> **Take‑away:** Binary addition follows the same carry rules as decimal but with base 2 digits.

---

### 5 Key Concepts Recap

* **Binary Encoding** – Two symbols (0, 1) are sufficient to represent any data through combinations.
* **Character Codes** – ASCII, Unicode, etc., map characters to numeric values.
* **Arithmetic Logic Unit (ALU)** – Hardware block that performs binary arithmetic & logic on encoded data.

---

### 6 Check Your Understanding

1. What binary pattern represents the ASCII character `C` (decimal 67)?
2. Perform the binary subtraction `1011₂ – 0101₂` and state the decimal result.
3. Why is binary preferred in digital electronics over a base‑10 system?

---

*Binary may look cryptic, but it’s simply the computer’s alphabet—master it, and the machine’s language opens up to you.*
