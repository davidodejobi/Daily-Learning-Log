# IFT 212 – Week 1 Reading Notes

## Introduction to Computer Architecture

### 1  Learning Objectives

By the end of this reading you should be able to:

* **Define** computer architecture in plain language.
* **Identify** and **explain** the role of key hardware components (CPU, buses, memory hierarchy, I/O).
* **Distinguish** between primary and secondary storage devices.
* **Describe** how historical milestones shaped today’s computers.
* **Use** basic performance formulas (IC, CPI, clock rate) to estimate run time.
* **Discuss** common design trade-offs (speed vs power, cost vs capacity).

---

### 2  What Is Computer Architecture?

Think of a computer as a tiny city. **Architecture** is its urban-planning blueprint—laying out roads (buses), neighbourhoods (CPU, memory, I/O), and rules of the road (instruction set) so people (data & instructions) can travel safely and efficiently. It covers:

1. **Structure** – what the parts are and how they connect.
2. **Organisation** – how those parts cooperate cycle-by-cycle.
3. **Implementation** – the electronic detail inside chips & boards.
4. **Performance** – the behaviour visible to programmers and users.

---

### 3  Why Does Architecture Matter?

* **Speed & Responsiveness** – determines how quickly tasks finish.
* **Energy & Heat** – affects battery life and cooling costs.
* **Scalability** – influences how easily we can add more cores, RAM, or storage later.
* **Compatibility** – ISA choices dictate which software we can run.
* **Cost** – smarter layouts can deliver more performance per dollar.

---

### 4  Component Overview (with Accessible Explanations)

| Component                              | Everyday Analogy                 | Core Function                                                                                                        | Extra Clarity                                                                                                                                      |
| -------------------------------------- | -------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CPU (Central Processing Unit)**      | Chef in a kitchen                | Fetches, decodes, and executes instructions; orchestrates all data movement.                                         | Inside are the **ALU** (does the maths & comparisons), **Control Unit** (recipe reader issuing steps), and **Registers** (quick-reach spice rack). |
| **System Bus**                         | Highway network                  | Carries data (cargo), addresses (street numbers), and control signals (traffic lights) between CPU, memory, and I/O. | Split into **Data Bus** (what is being moved), **Address Bus** (where it is going), **Control Bus** (when & how the move happens).                 |
| **Main Memory (RAM)**                  | Whiteboard                       | Temporarily holds the current task’s data/instructions; erases when power is off.                                    | Called **primary storage** because the CPU can reach it directly and quickly.                                                                      |
| **Cache (L1/L2/L3)**                   | Notepad in chef’s pocket         | Ultra-fast, tiny memories that keep *just-used* ingredients nearby to avoid trips back to RAM.                       |                                                                                                                                                    |
| **Secondary Storage (HDD/SSD)**        | Pantry or storeroom              | Holds software, documents, media permanently; slower but far larger than RAM.                                        |                                                                                                                                                    |
| **ROM / Firmware**                     | Cookbook stapled to the wall     | Contains start-up instructions (BIOS/UEFI) that never change during normal operation.                                |                                                                                                                                                    |
| **I/O Devices**                        | Doors & windows                  | Let the computer communicate with the outside world (keyboard, display, network, sensors).                           |                                                                                                                                                    |
| **ISA (Instruction Set Architecture)** | Common language                  | Defines the words (instructions) understood by both compilers and hardware.                                          |                                                                                                                                                    |
| **Parallel & Multicore**               | Several chefs sharing duties     | Multiple processing units working together for higher throughput.                                                    |                                                                                                                                                    |
| **Virtualisation & Security Blocks**   | Building security & guest passes | Provide isolated "rooms" (VMs, containers) and protect sensitive data inside the hardware.                           |                                                                                                                                                    |

---

### 5  Memory Hierarchy & Types

Computer memory forms a ladder from fastest/most expensive to slowest/cheapest:

1. **Registers** – nanoseconds; on-chip, per-core.
2. **Cache** – multi-level (L1, L2, L3).
3. **Main Memory (RAM)** – DRAM modules; primary, volatile.
4. **Secondary Storage** – SSD, HDD; non-volatile, high capacity.
5. **Offline Storage** – archival tape, optical discs, cloud.

Below are concise definitions to keep straight:

* **RAM (Random Access Memory)** – *Volatile* primary storage that the CPU can read/write in any order. Think of it as your active workspace—fast but forgetful when the power goes out.
* **ROM (Read-Only Memory)** – *Non-volatile* chips storing firmware. Contents persist and are largely unchangeable, guaranteeing the machine knows how to boot.
* **Cache (L1/L2/L3)** – Small SRAM blocks located on or close to the CPU die. Organised in levels: **L1** (per-core, \~32 KB, \~1 ns), **L2** (per-core or shared, \~256 KB), **L3** (shared, several MB). They exploit *temporal* & *spatial locality*—"if I used it once, I’ll likely use it soon or its neighbours."
* **Secondary Storage** – Large, *persistent* devices such as HDDs (magnetic platters) and SSDs (flash). Measured in milliseconds or microseconds, but you can store entire operating systems and media libraries.

> **Primary vs Secondary**: Primary storage (registers, cache, RAM) is directly addressable by the CPU and loses data when power is cut. Secondary keeps data even when off but needs controllers to move data into RAM first.

---

### 6  System Bus in Action

The **system bus** resembles a three-lane motorway:

1. **Data Bus** – the lane carrying the actual payload (bits).
2. **Address Bus** – signs indicating *which* memory location or device is being accessed.
3. **Control Bus** – traffic signals (read/write, clock, interrupt lines) coordinating the flow.
   Modern PCs often replace the traditional parallel bus with high-speed serial links (e.g., PCIe, NVMe) but the logical roles persist.

---

### 7  Historical Milestones (Expanded)

| Era           | Breakthrough                              | Explanation & Impact                                                                                                                                                                                           |
| ------------- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1940s–50s** | **Vacuum-tube giants & Von Neumann idea** | ENIAC & EDVAC introduced the stored-program concept: instructions live in the same memory as data, simplifying programming. Machines filled rooms and consumed megawatts.                                      |
| **1960s**     | **Transistors & Mainframes**              | IBM System/360 offered a family of compatible computers—a game-changer for software investment. Gordon Moore observed that transistor counts double \~every 2 years, foreshadowing relentless miniaturisation. |
| **1970s**     | **Microprocessor Revolution**             | Intel 4004 (1971) and 8086 (1978) squeezed the CPU onto a single chip, birthing personal computers and embedded systems.                                                                                       |
| **1980s**     | **RISC Philosophy & Graphical UIs**       | Research at Berkeley/Stanford showed simpler instructions executed faster (RISC). Meanwhile, Apple Macintosh popularised graphical interfaces, shifting workload from text to graphics.                        |
| **1990s**     | **Superscalar & Internet Era**            | CPUs began executing multiple instructions per cycle and added branch prediction. Networked PCs exploded, demanding faster servers and new I/O buses (PCI).                                                    |
| **2000s**     | **Multicore & Mobile**                    | Power limits stalled clock speeds, so chip makers packed many cores. ARM-based SoCs powered smartphones, emphasising energy efficiency.                                                                        |
| **2010s**     | **Cloud Computing & Accelerators**        | Data-centre-scale computing leveraged virtualisation; GPUs/TPUs accelerated AI workloads, sparking the deep-learning boom.                                                                                     |
| **2020s**     | **Edge AI & Quantum Experiments**         | Tiny neural processors run on IoT gadgets, while quantum bits promise future breakthroughs in specialised tasks.                                                                                               |

---

### 8  Measuring Performance

**Key Metrics**

* **Instruction Count (IC)** – number of instructions executed by a program.
* **Cycles per Instruction (CPI)** – average clock cycles each instruction needs on a given CPU for that workload.
* **Clock Rate (f)** – cycles per second (Hz).
* **CPU Time** – time spent on CPU = `IC × CPI / f`.

**Deriving Speed-up**

* **Amdahl’s Law** – The benefit of accelerating part of a workload is limited by the fraction that part represents.

> *Speed-up = 1 / \[(1 – p) + p/s]*  where *p* is the proportion improved, *s* is its speed-up.

**Detailed Example**
A media-editing program executes **800 M** instructions on CPU A with an average **CPI = 1.8** at **3 GHz**. What is the CPU time? If a new compiler reduces IC by 15 % but increases CPI to 2.0, which version is faster?

1. **Original**:
   CPU Time = 800 M × 1.8 / 3 GHz = 480 M / 3 G = **0.160 s**.
2. **Optimised**:
   New IC = 0.85 × 800 M = 680 M.
   CPU Time = 680 M × 2.0 / 3 GHz = 1 360 M / 3 G = **0.453 s**.
   Despite fewer instructions, the higher CPI makes it **2.8× slower**—an important reminder that all three variables matter.

> **Take-away:** Evaluate IC, CPI, and clock rate together rather than any single number.

---

### 9  Design Trade-Offs

| Trade-off                 | Why It Matters                                                                 | Typical Mitigations                                                    |
| ------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| Speed vs Power            | Faster clocks & more cores draw more current, heating batteries & datacentres. | Dynamic Voltage & Frequency Scaling (DVFS), big-.LITTLE architectures. |
| Cost vs Capacity          | Larger cache/memory increases silicon area & BOM.                              | Hierarchical caches, shared L3, off-chip DRAM.                         |
| Complexity vs Reliability | Superscalar & out-of-order logic is hard to verify, increasing bug risk.       | Simpler RISC cores, formal verification, micro-ops fusion.             |
| Latency vs Throughput     | Deep pipelines raise throughput but branch mispredict penalties hurt latency.  | Smarter predictors, shorter pipelines in low-power cores.              |

---

### 10  Self-Check (Quick Quiz)

1. Why is cache usually built from SRAM instead of DRAM?
2. Which bus line (data, address, control) would you widen to support >4 GB RAM on a 32-bit processor and why?
3. In the example above, name one way to regain the lost speed while keeping the lower instruction count.

---

### 11  Glossary

* **Firmware** – Low-level code stored in ROM that boots and configures hardware.
* **Locality (Temporal/Spatial)** – The tendency of a program to access the same data or nearby data repeatedly.
* **Superscalar** – CPU design that issues multiple instructions per cycle.
* **Pipelining** – Overlapping the stages of instruction execution for higher throughput.
* **Throughput vs Latency** – Completed work per unit time vs time to finish a single task.

---

### 12  Further Reading & Exploration

* Patterson & Hennessy – *Computer Organization and Design* (sections 1–3).
* Harris & Harris – *Digital Design and Computer Architecture* (chap. 1).
* Real-world teardown videos of modern smartphones (see how SoCs integrate CPU, GPU, RAM).

> *“Great architecture is invisible—users simply feel speed, reliability, and delight.”*
