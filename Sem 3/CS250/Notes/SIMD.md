Opened 12-13-2025 22:16

Status:

Tags: cs250

Topic: 9

Prev note: [[Processor Architecture]] Next Note: [[MIMD]]
# SIMD
> Single Instruction stream applied to Multiple Data streams.

- One program
- Many data elements processed in parallel
    



---
## 1 SIMD Structure

### Control Unit (CU)
- Instruction fetch and decode
- Instruction memory
- Broadcasts decoded instructions
    

### Processing Elements (PEs)
- Execute EX / MEM / WB stages
- Each has local data memory
    

---

## SIMD Execution Model
- CU broadcasts instructions
- All PEs receive the same instruction
- Each PE operates on its own data
    

---

## 2 Control Flow in SIMD: PE Enable Stack
- Each PE has a 1-bit enable stack
- Determines whether the PE executes non-control instructions
    

### Stack Operations
- **push**: normal push
- **push***: pushes (A' AND PT) → ELSE path
- **push****: pushes (A AND PT) → IF path




---
## 3 Conditional Execution
- if / else handled by enable stack masking
- Nested conditionals supported
- Control-heavy code reduces SIMD efficiency
    

---

## 4 SIMD Pros and Cons

### Advantages
- Single program copy
- No explicit synchronization
- High throughput for data-parallel code
    

### Disadvantages
- Inefficient for divergent control flow
- Complex conditional handling



# Active Recall
# References