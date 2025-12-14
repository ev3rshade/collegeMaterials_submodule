10-30-2025 12:40

Status:

Tags: cs250

Topic: 6

Prev note: [[Clocking and Timing]]  Next note: [[Datapath]]
# Instruction Pipelining
> overlapping execution of multiple instructions by dividing instruction execution into stages.



---
## 2 Classic 5-Stage Pipeline
1. **IF** – Instruction Fetch
2. **ID** – Instruction Decode & Register Read
3. **EX** – Execute / Address Calculation
4. **MEM** – Data Memory Access
5. **WB** – Write Back




---
## 3 Pipeline Performance

Ideal execution time for $n$ instructions in a $k$ stage pipeline (no stalls)
$$
\text{Clock Cycles } = n + k - 1
$$

### Pipeline Latency vs Throughput
- **Latency**: time for one instruction to complete
- **Throughput**: number of instructions completed per cycle




---
## 4 Pipeline Hazard and Stalls
Caused by Data Dependency (see Tags)

### Types of Hazards
#### Structural Hazard
>Occur when hardware resources are insufficient to support all active pipeline stages.
#### Data Hazard
> (data race) Occur when an instruction depends on the result of a previous instruction.
- **RAW (Read Access Write)** - true dependency
- **WAR (Write Access Read)** - name dependency
- **WAW (Write After Write)**

##### Load-use data hazard
- A special RAW hazard where data from memory is not available in time for the next instruction.



### Methods to resolve Hazards
#### Instruction reordering
- Compiler rearranges instructions to avoid data dependencies
- Preserves program correctness while improving pipeline flow
#### Forwarding (bypassing)
> Resolves data hazards by sending results directly from pipeline registers to dependent stages.
- Avoids waiting for write-back stage
- Common forwarding paths:
    - EX/MEM → EX
    - MEM/WB → EX

Forwarding scenarios
![[Screenshot 2025-12-10 013459.png]]
#### Pipeline stall (bubble)
> Temporarily halts pipeline progress to wait for data or control resolution.
- Implemented using **NOPs** (No Operation instructions)
- NOP changes no architectural state

#### Branch Prediction (1-bit)
> Resolves control hazards by guessing branch outcomes.
- Execution proceeds based on prediction
- 0 for taken
- 1 for not taken
- wrong prediction --> flip bit, flush pipeline
- Problem 8 [[CS250 Lab10 Processor Design.pdf]]

#### Dynamic Branch Prediction (2-bit)
- 2 bit is the most common implementation
- Uses runtime behavior
- **Branch Prediction Buffer (Branch History Table)**:
    - Indexed by lower bits of branch instruction address
    - Stores recent taken/not-taken outcomes
- States ![[6 Full Notes/College Notes/Sem 3/CS250/attachments/Screenshot 2025-12-10 014144.png]]

###### Higher branch prediction models
**Branch Target Buffer (BTB)**
- Caches destination PC or target instruction for branches
	- Tag-based structure
	- More costly than simple prediction buffers

**Correlating Predictor**
- Uses both local branch behavior and global execution history.

**Tournament Predictor**
- Combines multiple predictors and dynamically selects the best one.

### Hazard Detection Notation

Used in hardware to identify forwarding or stall conditions:
- **1a.** EX/MEM.RegisterRd = ID/EX.RegisterRn1
- **1b.** EX/MEM.RegisterRd = ID/EX.RegisterRm2
- **2a.** MEM/WB.RegisterRd = ID/EX.RegisterRn1
- **2b.** MEM/WB.RegisterRd = ID/EX.RegisterRm2
    

Where:
- **Rn1** = first source operand
- **Rm2** = second source operand

### Exceptions in Pipelines
> Pipelined implementations treat **exceptions** as a form of control hazard.
- Instructions after the faulting instruction must not complete
- Requires precise exception handling





---
## 5 Fallacies and Pitfalls (4.14)
### Fallacies
- Pipelining is easy
- Pipelining ideas are independent of technology

> In reality, technology changes pipeline depth, hazard behavior, and mitigation techniques.

### Pitfalls
- Instruction set design can severely impact pipeline efficiency



---
# References
Lab 08
[[CS250 Lab10 Processor Design.pdf]]