Opened 20:15

Status: 

Tags: [[CS250 Computer Architecture - Class Outline]]

Prev Topic: [[🟡 3 Instruction Sets]] Next Topic: [[🟡 5 Program Execution]]

Prev Note: Next Note: [[🟡 Compilation]]


# Program
> a set of instructions for a computer to perform a specific task


## 1 Language

### 1.1 Machine Language
> binary representation of machine instructions

### 1.2 [[Assembly]]


### 1.3 High-Level Language
> portable language
- Java
	- **Java Bytecode** - instruction from an instruction set designed to interpret Java programs
	- **Java Virtual Machine (JVM)** - the program that interprets Java bytecodes
	- **Just In Time Complier (JIT)** - The name commonly given to a computer that operates at runtime, translating the interpreted code segments into the native code of the computer
- C/C++



---
## 2 Program Translation
### High-Level Language Program (C)
- Written in a language designed for human readability
- Not directly executable by hardware
    

→ [[🟡 Compilation]]

### Assembly Language Program
- Architecture-specific, symbolic representation of machine instructions
- One-to-one (mostly) with machine instructions
    

→ **Assembly**

### Object File (Machine Language Module)
- Contains machine instructions and data
- May include:
    - Symbol table
    - Relocation information
    - Debugging information
        

Object files are often combined with:

- **Library routines** (also object files)
    

→ [[Linker]]

### Executable File
> A fully linked machine-language program with no unresolved references.
- Ready to run
- May still contain symbol tables or debugging information
- **Stipped executable**: debugging and symbol info removed

→ [[Loader]]

### Program in Memory
- Instructions and data are placed into main memory
- Execution begins at a defined entry point



---
## 3 Stored Program Concept
> The idea that **instructions (program)** and **data** are stored together in the _same main memory_.

- Fundamental principle of modern computers
- Enables programs to be treated as data
    

### Program Counter (PC)

> A register that holds the address of the current instruction being executed.

- Automatically updated after each instruction
- **LEGv8**: instructions are 32 bits (4 bytes), so the PC normally increments by **4 bytes**




---
## 4 What Makes Up a Program

### Instructions
#### Procedures (Functions)
> A **procedure** is a stored subroutine that performs a specific task using parameters provided by the caller and may return a result.

Benefits:
- Abstraction
- Code reuse
- Easier debugging and maintenance
    

#### Branch-and-Link Instruction

> An instruction that branches to a target address **and saves the return address**.

- In **LEGv8**:
    - Return address stored in **LR (X30)**
    - Instruction following the call is saved
        

**Return** from a procedure:

```
BR LR
```

#### Basic block
> a sequence of instructions without branches


### Caller and Callee
- **Caller**: the code that invokes a procedure and supplies arguments
- **Callee**: the procedure being executed
    

Responsibilities (simplified):
- Caller: passes arguments, saves temporary registers if needed
- Callee: saves/restores registers it uses and returns control






---
## 5 Memory and Registers for Procedures

### Register Purposes

| Registers | Name                | Used For                  | Preserved |
| --------- | ------------------- | ------------------------- | --------- |
| X0–X7     | Arguments / Results | Parameters, return values | ❌         |
| X8        | Indirect result     | Large returns             | ❌         |
| X9–X15    | Temporaries         | Scratch values            | ❌         |
| X16–X17   | IP0/IP1             | Linker / temp             | ❌         |
| X18       | Platform            | OS-specific               | ❌         |
| X19–X27   | Saved               | Long-lived values         | ✅         |
| X28       | SP                  | Stack pointer             | ✅         |
| X29       | FP                  | Frame pointer             | ✅         |
| X30       | LR                  | Return address            | ✅         |
| X31       | XZR                 | Constant zero             | N/A       |


### Stack
> A region of memory used to support procedure calls and local storage.

- Grows **downward** (toward lower addresses)
- Space is allocated by **subtracting from SP**
    

#### Stack Pointer (SP)
> Register that points to the most recently allocated location on the stack.

Used for:
- Saving registers (spilling)
- Storing local variables
- Creating procedure frames
    

#### Push and Pop
- **Push**: decrement SP, then store data
- **Pop**: load data, then increment SP
    

---
#### Procedure Frame (Activation Record)
> The portion of the stack allocated for one procedure call.

Contains:
- Saved registers
- Local variables
- Return address (if needed)
    

Each procedure call creates a new frame.


### Frame Pointer (FP)
> A register that points to a fixed location within the current procedure frame.

- Makes access to locals and saved registers easier
- Especially useful when SP changes during execution
    

### Global Pointer (GP)
> A register reserved to point to the **static/global data area**.
- Used for global variables
- Allows efficient access to statically allocated data
    


### Heap
> A region of memory used for **dynamic allocation** (e.g., `malloc`).
- Grows upward
- Managed at runtime
- Not automatically freed when procedures return
    

---
## 6 Libraries

### Dynamically Linked Libraries (DLLs)

> Library routines that are linked to a program **during execution** rather than at compile time.

Advantages:
- Smaller executable size
- Shared library code in memory
- Easier updates



---
# References
## Textbook
- Chapter 2
	- 2.8

## Labs
[[CS250 Lab07 Program Compilation.pdf]]