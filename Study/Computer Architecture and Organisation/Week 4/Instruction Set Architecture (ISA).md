# Detailed Study Notes

## 1) What ISA Is and Why It Matters

- The Instruction Set Architecture is the part of computer architecture visible to programmers. It defines the machine language a CPU can execute, including instructions, native data types, registers, memory model, I/O, and how interrupts and exceptions are handled.
    
- At a high level, the ISA is the contract between software and hardware. Compilers target the ISA, and microarchitectures implement it.
    

## 2) Scope of the ISA

An ISA typically answers three big questions:

1. **Operand storage**: Where are operands held besides main memory? Can ALU operands live in memory or must they be in registers first? What is the address space and addressability?
    
2. **Register set**: How many registers exist, what size are they, and how are they used (data, addresses, temporaries, control)?
    
3. **Instruction set**: What operations (opcodes) are provided, what addressing modes exist, and how many operands can be named in an instruction?
    

---

## 3) Goals for Instruction-Set Design

- **Minimize instruction length** to improve code density and fetch bandwidth.
    
- **Maximize flexibility** so that compilers can generate efficient code across many patterns.
    
- **Leverage compilers** when choosing features such as addressing modes and instruction forms.
    
- **Define how operands are addressed**, since addressing modes strongly influence code size and performance.
    

### Practical design tradeoffs

- **Shorter instructions** save space and can improve fetch rate, but limit opcode space and operand fields.
    
- **Fixed-length vs variable-length** instructions: fixed length is easier to decode but may waste space; variable length can be denser but complicates decoding and alignment.
    
- **Instruction format** is shaped by memory organization. Even with 16-, 32-, or 64-bit words, byte addressability is often preferred so each byte has a unique address. A fixed overall length can still allow a variable-size opcode field (expanding opcode).
    

---

## 4) Instruction Formats and Operand Counts

Every machine instruction carries at least:

- **Opcode field**: which operation to perform.
    
- **Address/operand field(s)**: where to find the source operands and where to place the result.
    

### Common operand-count formats

- **Zero-address**: stack-based; operands are implied on the stack. Example operations like `ADD` pop two values, push result.
    
- **One-address**: accumulator based; the accumulator is an implicit operand and destination.
    
- **Two-address**: typically one source is also the destination register.
    
- **Three-address**: two sources and a distinct destination, usually registers.
    

### Worked example for the expression Z=(X⋅Y)+(W⋅U)Z = (X·Y) + (W·U)

**Three-address form**

```
Mult  R1, X, Y    ; R1 = X·Y
Mult  R2, W, U    ; R2 = W·U
Add   Z,  R2, R1  ; Z  = R2 + R1
```

**Two-address form**

```
Load  R1, X       ; R1 = X
Mult  R1, Y       ; R1 = X·Y
Load  R2, W       ; R2 = W
Mult  R2, U       ; R2 = W·U
Add   R1, R2      ; R1 = (X·Y) + (W·U)
Store Z,  R1      ; Z  = R1
```

**One-address (accumulator) form**

```
Load  X           ; ACC = X
Mult  Y           ; ACC = X·Y
Store Temp        ; Temp = X·Y
Load  W           ; ACC = W
Mult  U           ; ACC = W·U
Add   Temp        ; ACC = (W·U) + (X·Y)
Store Z           ; Z = ACC
```

**Zero-address (stack) form**

```
Push  X           ; [X]
Push  Y           ; [X, Y]
Mult              ; [X·Y]
Push  W           ; [X·Y, W]
Push  U           ; [X·Y, W, U]
Mult              ; [X·Y, W·U]
Add               ; [(X·Y) + (W·U)]
Store Z           ; Z = top
```

---

## 5) Address Space and Addressability

- **Address space**: how many unique locations the ISA can address, which sets an upper bound on maximum memory.
    
- **Addressability**: the granularity of addressing (for example, byte-addressable). Byte addressability simplifies character access and unaligned data but can add complexity to alignment and performance.
    

---

## 6) How CPUs Organize Operands: Three Classic Models

|Model|Where operands live|Characteristics|Pros|Cons|
|---|---|---|---|---|
|**Stack**|Top of an implicit stack|Zero-address instructions dominate. Operators pop operands and push results. Suits postfix (RPN) evaluation.|Very compact code, simple expression evaluation|Poor random access, stack becomes a bottleneck, harder for optimizing compilers|
|**Accumulator**|An implicit accumulator register|One-address instructions; accumulator is the implicit destination and usually one source|Short instructions, small code|High memory traffic, accumulator is only temporary storage|
|**General-Purpose Registers (GPR)**|Named registers and memory|Two- or three-address styles; compilers allocate values to registers|Easier code generation, values can remain in registers longer, fits modern pipelines|More bits per instruction to name registers, longer fetch and decode, pressure on register file|

### Stack and RPN

- Reverse Polish Notation places operators after operands (postfix), which eliminates the need for parentheses and maps naturally to stack execution. Example: `(X + Y) × (W − Z) + 2` becomes `X Y + W Z − × 2 +` on a stack machine.
    

### Choosing among models

- When **memory is slow** relative to registers, GPR designs dominate in practice, which is why most modern CPUs are register rich.
    

---

## 7) Designing Instruction Formats: Practical Factors

When selecting instruction formats, consider:

1. The number of distinct instructions to represent.
    
2. Addressability and available addressing modes.
    
3. Ease of decoding for the hardware.
    
4. Whether fields are fixed width or variable width.
    
5. Hardware cost to decode and execute.
    

---

## 8) Mid-lesson Checks (with answers)

- **Which component pertains to native machine language?** Instruction Set Architecture (ISA).
    
- **Which issue is primarily addressed by ISA in the lesson?** The register set and its organization and capabilities.
    

---

## 9) Key Takeaways

- ISA defines the programmer’s model of the machine and its instruction vocabulary.
    
- Operand storage, register organization, and instruction formats are core to ISA design.
    
- Instruction-length, format, and addressing-mode choices create concrete tradeoffs among code density, decode simplicity, and performance.
    
- Stack, accumulator, and GPR organizations each shape instruction formats and compiler strategies. Modern designs favor GPR due to speed and flexibility.
    

---

## 10) Suggested Reading

- Patterson and Hennessy, _Computer Organization and Design_.
    
- Harris and Harris, _Digital Design and Computer Architecture_.