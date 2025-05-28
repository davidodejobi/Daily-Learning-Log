# IFT 212 – Week 1

## Introduction to Computer Architecture

### 1. What is Computer Architecture?

Computer architecture is the *blueprint* that specifies a computer’s internal structure, organization, and functionality. It determines **how** the hardware components fit together, interact, and ultimately influence performance, cost, power usage, and scalability.

> **Analogy:** Just as a house has rooms designed for specific tasks, a computer has specialised components (CPU, memory, I/O, etc.) wired together in a purposeful layout.

### 2. Why Does Architecture Matter?

* **Performance** – Defines how quickly data is processed and tasks are completed.
* **Capacity** – Sets practical limits on memory size, storage, and throughput.
* **Compatibility & Upgradability** – A clear architecture supports modular upgrades (e.g., adding RAM, swapping CPUs).
* **Energy Efficiency** – Good architectural choices balance speed with power consumption.
* **Cost & Physical Constraints** – Guides trade‑offs in chip area, heat dissipation, and manufacturing budget.

### 3. Historical Snapshot

| Generation        | Key Technology      | Architectural Leap                   | Example        |
| ----------------- | ------------------- | ------------------------------------ | -------------- |
| 1st (1940s–50s)   | Vacuum tubes        | Fixed‑program control                | ENIAC          |
| 2nd (1950s–60s)   | Transistors         | Smaller, more reliable               | IBM 7090       |
| 3rd (1960s–70s)   | Integrated Circuits | SSI/MSI chips                        | PDP‑11         |
| 4th (1970s–90s)   | Microprocessors     | CPU on a single chip                 | Intel 8086     |
| 5th (2000s–today) | Multicore & SoC     | Parallelism, on‑chip cache hierarchy | Apple M‑series |

*(Video note: “Computers have come a long way…”)*

### 4. Core Hardware Components

| Component                         | Purpose                                                                        | Key Notes from the Video                                                |
| --------------------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------- |
| **CPU (Central Processing Unit)** | Executes instructions, performs arithmetic/logic, orchestrates data flow.      | Called the *brain* of the computer. Consists of ALU, CU, and registers. |
| **ALU (Arithmetic Logic Unit)**   | Basic maths & logic operations.                                                |                                                                         |
| **Control Unit (CU)**             | Decodes instructions, directs component interactions.                          |                                                                         |
| **Registers**                     | Ultra‑fast temporary storage inside CPU.                                       |                                                                         |
| **Main Memory (RAM)**             | Volatile storage for active data/programs.                                     | Faster than disks; directly accessible by CPU.                          |
| **Cache**                         | Small, very fast memory between CPU & RAM.                                     | Bridges speed gap; reduces latency.                                     |
| **Secondary Storage**             | Non‑volatile disks/SSDs hold data long‑term.                                   |                                                                         |
| **I/O Devices**                   | Interfaces for user & external systems.                                        | Keyboards, screens, network cards, sensors, etc.                        |
| **System Bus**                    | Parallel set of wires (data, address, control lines) linking CPU, memory, I/O. | Compared to a highway connecting cities.                                |

### 4A. Software Stack & Types

Computer architecture does not stand alone; a layered software stack turns the raw hardware into a usable system:

| Layer                                  | Purpose                                                                                                                | Examples                                                                      |                          |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ------------------------ |
| **Microcode / Firmware**               | Lowest‑level control instructions stored in ROM/Flash; initializes hardware and offers foundational routines.          | BIOS/UEFI, embedded controller code                                           | -                        |
| **Operating System (System Software)** | Abstracts hardware into high‑level resources (processes, files, virtual memory) and manages I/O, security, scheduling. | Windows, Linux, macOS, Android                                                | Mentioned in the lecture |
| **Utility & Toolchain Software**       | Bridges programmers and hardware by translating human‑readable code into machine code or by managing binaries.         | Compilers (GCC, Clang), Assemblers, Linkers, Loaders, Interpreters, Debuggers | -                        |
| **Middleware / Virtualization**        | Provides additional runtime services or isolates guests from host hardware.                                            | JVM, .NET CLR, Docker Engine, Hyper‑V, VMware ESXi                            | -                        |
| **Application Software**               | Delivers user‑facing functionality that ultimately generates the workload the architecture must support.               | Browsers, Databases, Games, Office Suites                                     | Mentioned in the lecture |

*Video call‑out:* "From firmware all the way up to your favorite app, each software layer leverages the architectural decisions made in silicon."

**Design implications:**

* ISA defines what compilers can generate.
* OS scheduling interacts with CPU core count & cache hierarchy.
* Virtualization relies on hardware support (VT‑x, ARM‑VE).
* Application performance hinges on the efficiency of lower layers.

---

### 5. Design Principles Highlighted

1. **Performance/Throughput** – maximise instruction‑per‑cycle (IPC) & clock rate.
2. **Modularity** – break complex designs into smaller manageable blocks (building‑block concept).
3. **Scalability** – support future cores, memory size, peripheral growth.
4. **Efficiency** – strike balance between speed, area, power (video: “We want computers to be as fast and energy‑efficient as possible”).
5. **Reliability & Fault Tolerance** – error detection/correction, redundancy.

### 6. Putting It All Together

* Instructions fetched from memory are decoded in the CPU.
* Data travels via the system bus between CPU, RAM, and I/O.
* The architecture dictates how wide the bus is, cache hierarchy levels, and supported instruction sets (e.g., RISC‑V, x86‑64, ARM).

### 7. Why This Matters to You as a Technologist

* **Programmers** write more efficient code when they understand caches, pipelining, and parallelism.
* **Hardware Engineers** design chips & boards that meet target constraints.
* **System Integrators** choose compatible components and optimise configurations.

### 8. Quick Self‑Check

1. Name the three major sub‑units inside a CPU and their primary roles.
2. Explain the analogy of the system bus and why bandwidth matters.
3. Describe two trade‑offs architects face when increasing performance.

---

### 9. Key Terms Glossary

* **Clock Cycle** – Smallest time unit of CPU activity.
* **Instruction Set Architecture (ISA)** – The agreed language understood by hardware & compilers.
* **Pipelining** – Overlapping instruction stages for higher throughput.
* **Latency vs Throughput** – Delay for one task vs tasks completed per unit time.

---

*“Understanding computer architecture is essential for anyone interested in building, programming, or even just using computers.” – Week 1 video*
