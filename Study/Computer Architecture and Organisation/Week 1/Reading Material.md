# IFT 212 – Week 1 Reading Notes

## Introduction to Computer Architecture

### 1  Learning Objectives

By the end of this reading you should be able to:

* **Define** computer architecture in plain language.
* **Identify** and **explain** the role of key hardware components (CPU, buses, memory hierarchy, I/O).
* **Distinguish** between primary and secondary storage devices.
* **Describe** how historical milestones shaped today’s computers.
* **Use** basic performance formulas (IC, CPI, clock rate) to estimate run time.
* **Discuss** common design trade‑offs (speed vs power, cost vs capacity).

---

### 2  What Is Computer Architecture?

Think of a computer as a tiny city. **Architecture** is its urban‑planning blueprint—laying out roads (buses), neighbourhoods (CPU, memory, I/O), and rules of the road (instruction set) so people (data & instructions) can travel safely and efficiently. It covers:

1. **Structure** – what the parts are and how they connect.
2. **Organisation** – how those parts cooperate cycle‑by‑cycle.
3. **Implementation** – the electronic detail inside chips & boards.
4. **Performance** – the behaviour visible to programmers and users.

---

### 3  Why Does Architecture Matter?

* **Speed & Responsiveness** – determines how quickly tasks finish.
* **Energy & Heat** – affects battery life and cooling costs.
* **Scalability** – influences how easily we can add more cores, RAM, or storage later.
* **Compatibility** – ISA choices dictate which software we can run.
* **Cost** – smarter layouts can deliver more performance per dollar.

---

### 4  Component Overview (with Accessible Explanations)

| Component                              | Everyday Analogy                 | Core Function                                                                                                        | Extra Clarity                                                                                                                                      |
| -------------------------------------- | -------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CPU (Central Processing Unit)**      | Chef in a kitchen                | Fetches, decodes, and executes instructions; orchestrates all data movement.                                         | Inside are the **ALU** (does the maths & comparisons), **Control Unit** (recipe reader issuing steps), and **Registers** (quick‑reach spice rack). |
| **System Bus**                         | Highway network                  | Carries data (cargo), addresses (street numbers), and control signals (traffic lights) between CPU, memory, and I/O. | Split into **Data Bus** (what is being moved), **Address Bus** (where it is going), **Control Bus** (when & how the move happens).                 |
| **Main Memory (RAM)**                  | Whiteboard                       | Temporarily holds the current task’s data/instructions; erases when power is off.                                    | Called **primary storage** because the CPU can reach it directly and quickly.                                                                      |
| **Cache (L1/L2/L3)**                   | Notepad in chef’s pocket         | Ultra‑fast, tiny memories that keep *just‑used* ingredients nearby to avoid trips back to RAM.                       |                                                                                                                                                    |
| **Secondary Storage (HDD/SSD)**        | Pantry or storeroom              | Holds software, documents, media permanently; slower but far larger than RAM.                                        |                                                                                                                                                    |
| **ROM / Firmware**                     | Cookbook stapled to the wall     | Contains start‑up instructions (BIOS/UEFI) that never change during normal operation.                                |                                                                                                                                                    |
| **I/O Devices**                        | Doors & windows                  | Let the computer communicate with the outside world (keyboard, display, network, sensors).                           |                                                                                                                                                    |
| **ISA (Instruction Set Architecture)** | Common language                  | Defines the words (instructions) understood by both compilers and hardware.                                          |                                                                                                                                                    |
| **Parallel & Multicore**               | Several chefs sharing duties     | Multiple processing units working together for higher throughput.                                                    |                                                                                                                                                    |
| **Virtualisation & Security Blocks**   | Building security & guest passes | Provide isolated "rooms" (VMs, containers) and protect sensitive data inside the hardware.                           |                                                                                                                                                    |

---

### 5  Memory Hierarchy & Types

Computer memory forms a ladder from fastest/most expensive to slowest/cheapest:

1. **Registers** – nanoseconds; on‑chip, per‑core.
2. **Cache** – multi‑level (L1, L2, L3).
3. **Main Memory (RAM)** – DRAM modules; primary, volatile.
4. **Secondary Storage** – SSD, HDD; non‑volatile, high capacity.
5. **Offline Storage** – archival tape, optical discs, cloud.

Below are concise definitions to keep straight:

* **RAM (Random Access Memory)** – *Volatile* primary storage that the CPU can read/write in any order. Think of it as your active workspace—fast but forgetful when the power goes out.
* **ROM (Read‑Only Memory)** – *Non‑volatile* chips storing firmware. Contents persist and are largely unchangeable, guaranteeing the machine knows how to boot.
* **Cache (L1/L2/L3)** – Small SRAM blocks located on or close to the CPU die. Organised in levels: **L1** (per‑core, \~32 KB, \~1 ns), **L2** (per‑core or shared, \~256 KB), **L3** (shared, several MB). They exploit *temporal* & *spatial locality*—"if I used it once, I’ll likely use it soon or its neighbours."
* **Secondary Storage** – Large, *persistent* devices such as HDDs (magnetic platters) and SSDs (flash). Measured in milliseconds or microseconds, but you can store entire operating systems and media libraries.

> **Primary vs Secondary**: Primary storage (registers, cache, RAM) is directly addressable by the CPU and loses data when power is cut. Secondary keeps data even when off but needs controllers to move data into RAM first.

---

### 6  System Bus in Action

The **system bus** resembles a three‑lane motorway:

1. **Data Bus** – the lane carrying the actual payload (bits).
2. **Address Bus** – signs indicating *which* memory location or device is being accessed.
3. **Control Bus** – traffic signals (read/write, clock, interrupt lines) coordinating the flow.
   Modern PCs often replace the traditional parallel bus with high‑speed serial links (e.g., PCIe, NVMe) but the logical roles persist.

---

### 7  Historical Milestones (Expanded)

| Era           | Breakthrough                              | Explanation & Impact                                                                                                                                                                                           |
| ------------- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1940s–50s** | **Vacuum‑tube giants & Von Neumann idea** | ENIAC & EDVAC introduced the stored‑program concept: instructions live in the same memory as data, simplifying programming. Machines filled rooms and consumed megawatts.                                      |
| **1960s**     | **Transistors & Mainframes**              | IBM System/360 offered a family of compatible computers—a game‑changer for software investment. Gordon Moore observed that transistor counts double \~every 2 years, foreshadowing relentless miniaturisation. |
| **1970s**     | **Microprocessor Revolution**             | Intel 4004 (1971) and 8086 (1978) squeezed the CPU onto a single chip, birthing personal computers and embedded systems.                                                                                       |
| **1980s**     | **RISC Philosophy & Graphical UIs**       | Research at Berkeley/Stanford showed simpler instructions executed faster (RISC). Meanwhile, Apple Macintosh popularised graphical interfaces, shifting workload from text to graphics.                        |
| **1990s**     | **Superscalar & Internet Era**            | CPUs began executing multiple instructions per cycle and added branch prediction. Networked PCs exploded, demanding faster servers and new I/O buses (PCI).                                                    |
| **2000s**     | **Multicore & Mobile**                    | Power limits stalled clock speeds, so chip makers packed many cores. ARM‑based SoCs powered smartphones, emphasising energy efficiency.                                                                        |
| **2010s**     | **Cloud Computing & Accelerators**        | Data‑centre‑scale computing leveraged virtualisation; GPUs/TPUs accelerated AI workloads, sparking the deep‑learning boom.                                                                                     |
| **2020s**     | **Edge AI & Quantum Experiments**         | Tiny neural processors run on IoT gadgets, while quantum bits promise future breakthroughs in specialised tasks.                                                                                               |

---

### 8  Measuring Performance (Expanded)

Performance measurement in computing is like timing a production line—both **how fast each step occurs** and **how many steps are required** matter. Two complementary views dominate:

1. **Throughput** – total work finished per unit time (e.g., transactions / second).
2. **Latency** – time to finish one job (e.g., seconds / query).

Below we break down the basic variables, derive formulas, and work through two fully‑annotated examples.

#### 8.1 Key Terms & Units

| Symbol       | Name                   | Typical Unit    | What it Represents                   |
| ------------ | ---------------------- | --------------- | ------------------------------------ |
| **IC**       | Instruction Count      | instructions    | Dynamic count executed by a program  |
| **CPI**      | Cycles‑Per‑Instruction | cycles / inst.  | Avg. hardware effort per instruction |
| **f**        | Clock Rate             | Hz (cycles / s) | CPU oscillation frequency            |
| **T\_clk**   | Clock Cycle Time       | seconds / cycle | *T\_clk = 1 / f*                     |
| **CPU Time** | Execution Time         | seconds         | Time CPU spends on the task only     |

The core relationship:

> **CPU Time = IC × CPI × T\_clk   or   IC × CPI / f**

*Why two forms?*  Because sometimes datasheets give frequency (f) and other times give period (T\_clk). Use whichever you have.

#### 8.2 Breaking Down CPI

CPI is an *average*. For real programs different instruction types take different cycles. We compute **overall CPI** via a weighted average:

```
CPI_overall = Σ (fraction_i × CPI_i)
```

where *fraction\_i* is the percentage of dynamic instructions of type (i).

#### 8.3 Step‑by‑Step Example 1 (Single‑class)\*

> **Given:**
> – IC = 500 000 instructions
> – Average CPI = 2 cycles/inst.
> – Each clock cycle takes 0.5 ns
> **Find:** CPU Time

1. **Total clock cycles**    = IC × CPI                   
      = 500 000 × 2 = 1 000 000 cycles
2. **CPU Time**          = Total cycles × T\_clk
      = 1 000 000 × 0.5 ns
      = 500 000 ns
3. **Convert to ms**     = 500 000 ns ÷ 1 000 000
      = **0.5 ms**

> **Answer:** The CPU needs 0.5 milliseconds to finish the program.

#### 8.4 Step‑by‑Step Example 2 (Multi‑class)\*

We ran a benchmark on Machine A (200 MHz clock) and observed:

| Instruction Class | Occurrence (%) | CPI\_i (cycles) |
| ----------------- | -------------- | --------------- |
| ALU               | 38 %           | 1               |
| Load/Store        | 15 %           | 3               |
| Branch            | 42 %           | 4               |
| Others            | 5 %            | 5               |

Compute overall CPI and execution time for 100 instructions.

**1 – Overall CPI** (weighted):

```
CPI = (0.38×1) + (0.15×3) + (0.42×4) + (0.05×5)
    = 0.38 + 0.45 + 1.68 + 0.25
    = 2.76 cycles/inst.
```

**2 – Total cycles for 100 instructions:**

```
Total cycles = 100 × 2.76 = 276 cycles
```

**3 – Clock period (T\_clk):**

```
f = 200 MHz ⇒ T_clk = 1 / 200 × 10⁶ = 5 ns
```

**4 – CPU Time:**

```
CPU Time = 276 cycles × 5 ns = 1380 ns = 1.38 µs
```

> **Answer:** Overall CPI = 2.76; executing 100 instructions takes roughly **1.38 microseconds**.

#### 8.5 Amdahl’s Law Refresher

If a specific part (fraction *p*) of a workload is sped‑up by factor *s*, the total speed‑up is:

```
Speed‑up_total = 1 / ((1 – p) + p/s)
```

*Example:* speeding a 30 % hotspot by 4× yields overall = **1 / (0.7 + 0.3/4) ≈ 1.48×**.

#### 8.6 Guidelines for Optimisation

* **Profile first** – identify high‑IC sections or high‑CPI instructions.
* **Lower IC** by algorithmic improvements or compiler optimisations.
* **Lower CPI** by choosing instructions that map to faster hardware units.
* **Raise f** (overclock/turbo) but be mindful of power and thermal limits.

---

### 9  Design Trade‑Offs  Design Trade‑Offs

| Trade‑off                 | Why It Matters                                                                 | Typical Mitigations                                                    |
| ------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| Speed vs Power            | Faster clocks & more cores draw more current, heating batteries & datacentres. | Dynamic Voltage & Frequency Scaling (DVFS), big‑.LITTLE architectures. |
| Cost vs Capacity          | Larger cache/memory increases silicon area & BOM.                              | Hierarchical caches, shared L3, off‑chip DRAM.                         |
| Complexity vs Reliability | Superscalar & out‑of‑order logic is hard to verify, increasing bug risk.       | Simpler RISC cores, formal verification, micro‑ops fusion.             |
| Latency vs Throughput     | Deep pipelines raise throughput but branch mispredict penalties hurt latency.  | Smarter predictors, shorter pipelines in low‑power cores.              |

---

### 10  Self‑Check (Quick Quiz)

1. Why is cache usually built from SRAM instead of DRAM?
2. Which bus line (data, address, control) would you widen to support >4 GB RAM on a 32‑bit processor and why?
3. In the example above, name one way to regain the lost speed while keeping the lower instruction count.

---

### 11  Glossary

* **Firmware** – Low‑level code stored in ROM that boots and configures hardware.
* **Locality (Temporal/Spatial)** – The tendency of a program to access the same data or nearby data repeatedly.
* **Superscalar** – CPU design that issues multiple instructions per cycle.
* **Pipelining** – Overlapping the stages of instruction execution for higher throughput.
* **Throughput vs Latency** – Completed work per unit time vs time to finish a single task.

---

### 12  Further Reading & Exploration

* Patterson & Hennessy – *Computer Organization and Design* (sections 1–3).
* Harris & Harris – *Digital Design and Computer Architecture* (chap. 1).
* Real‑world teardown videos of modern smartphones (see how SoCs integrate CPU, GPU, RAM).

> *“Great architecture is invisible—users simply feel speed, reliability, and delight.”*
