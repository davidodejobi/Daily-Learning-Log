# Cache Memory Worksheet

## Introduction

Have you ever wondered how your computer seems to instantly open a website you just visited or lets you switch apps in a flash? The secret is **cache memory**—a tiny, super‑fast organiser that keeps your most‑used data right at the CPU’s fingertips. Think of cache as the top drawer in your desk: you stash pens, sticky notes, and USB drives there so you don’t rummage through the big filing cabinet (main memory) every time.

This worksheet will guide you through:

1. Essential cache‑related vocabulary
2. Core mapping techniques
3. Practice exercises to cement understanding

By the end, you’ll be a cache‑memory whiz!

---

## A. Key Terms Cheat‑Sheet

| **Term**                  | **Definition (plain English)**                                                                                                    |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Cache Memory**          | A small, lightning‑fast storage area that keeps recently or frequently used data/instructions so the CPU can grab them instantly. |
| **Main Memory (RAM)**     | The computer’s primary work area—slower than cache but holds much more data.                                                      |
| **Block (or Cache Line)** | The fixed‑size chunk of data moved back and forth between cache and main memory.                                                  |
| **Block Size**            | How large one block is (in bytes or words).                                                                                       |
| **Cache Hit**             | When the CPU finds the needed data already inside the cache—high‑five, no delay!                                                  |
| **Cache Miss**            | When the needed data isn’t in the cache. The system must fetch it from RAM (slower).                                              |
| **Block Replacement**     | The policy for deciding which old block to kick out when a new one loads into a full cache.                                       |
| **Cache Mapping**         | The rulebook for choosing *where* each incoming main‑memory block can live in the cache.                                          |

---

## B. Cache Mapping Techniques

| Mapping Style         | One‑Sentence Idea                                                                     | Typical Use‑Case                                                                |
| --------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Direct‑Mapped**     | Every memory block has exactly one “home” line in the cache.                          | Simpler, cheaper hardware but more conflicts.                                   |
| **Fully Associative** | Any memory block may reside in *any* cache line.                                      | Flexible but needs lots of tag comparisons—costly.                              |
| **Set‑Associative**   | The cache is divided into sets; a block can go into any line *within* a specific set. | Sweet spot: fewer conflicts than direct‑mapped, cheaper than fully associative. |

---

## C. Worksheet Exercises

### 1. Matching Mania – Warm‑Up

Match each **Term** with the correct **Description**. Write the letter in the blank.

| # | Term              | Description                                             |
| - | ----------------- | ------------------------------------------------------- |
| 1 | Cache Memory      | a. The number of bytes/words moved per transfer.        |
| 2 | Block Replacement | b. Rapid storage for frequently used data.              |
| 3 | Cache Mapping     | c. Rule for choosing the cache slot for a memory block. |
| 4 | Block Size        | d. Rule for deciding which old cache entry to evict.    |

*Answer bank:* a, b, c, d

### 2. Hit or Miss?

In your own words (1–2 sentences each):

* **Cache Hit:** \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
* **Cache Miss:** \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 3. Name That Mapping

Fill in each blank with **Direct‑Mapped**, **Fully Associative**, or **Set‑Associative**.

1. A block has only *one* possible slot → \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
2. A block can go to *any* slot → \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
3. A block can go to *one of a few* slots in the same set → \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 4. Bonus Challenge

Briefly describe **one** common replacement policy (e.g., LRU, FIFO, Random). Why might a designer choose that policy?

```


```

---

## D. Answer Key

*(Fold or hide until students finish!)*

1. Matching: 1→b, 2→d, 3→c, 4→a
2. Hit/Miss Sample:

   * *Hit:* The requested data is already in the cache, so access is instant.
   * *Miss:* The data isn’t in cache; the CPU must fetch it from slower main memory first.
3. Mapping: 1) Direct‑Mapped, 2) Fully Associative, 3) Set‑Associative
4. Replacement Example: **LRU (Least Recently Used)** removes the block that hasn’t been accessed for the longest time, under the assumption it’s least likely to be needed soon.