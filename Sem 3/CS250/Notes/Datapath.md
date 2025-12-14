10-30-2025 01:10

Status: 

Tags: cs250

Topic: 6

Prev Note: [[Instruction Pipelining]] Next Note: [[🔴 8 Control and Task Management]]


# Datapath
>A **datapath** is the collection of hardware units that store, move, and operate on data within a processor.
>(path of data flow)

In the **LEGv8** architecture, the datapath defines the _path of data flow_ as instructions are fetched, decoded, executed, and completed.

A datapath works **together with the control unit**, which tells each component _what to do_ in a given clock cycle.





---
## 1 Datapath Elements
> (core datapath components)
> These elements together are called **datapath elements**.
### State Elements
#### Registers
- **Program Counter (PC)** – holds the address of the next instruction
- **Register File** – stores general-purpose registers used by instructions
    
#### Memory Units
- **Instruction Memory** – stores program instructions
- **Data Memory** – stores program data (used by load/store instructions)


### Combinatorial Elements
#### Functional Units
- **ALU (Arithmetic Logic Unit)** – performs arithmetic and logical operations
- **Adders** – used for PC incrementing and branch target calculation


#### Data Routing
- **Multiplexers (MUXes)** – select between multiple data inputs
- **Wires / buses** – carry data and control signals


Summary:
- Register file
- ALU
- Instruction memory
- Data memory
- Adders
- Multiplexers

a simple example
![[6 Full Notes/College Notes/Sem 3/CS250/attachments/Screenshot 2025-12-09 135243.png]]





---
## 2 Instruction Classes and Required Datapath Units

### R-format (ALU) Instructions
Required units
1. Register file (read operands)
2. ALU (perform operation)
    
3. Register file (write result)
    

### Load and Store Instructions
Required units:
1. Register file
2. ALU (compute effective address)
3. Data memory
4. Sign extension unit (offset)
5. Multiplexers and wiring

> The ALU always performs **addition** to compute memory addresses.

### Branch Instructions
Required units:
1. ALU – evaluates branch condition
2. Adder – computes branch target address
3. Program Counter (PC)
4. Multiplexer – selects next PC value
    
Branch target computation:
- Sign-extend immediate
- Shift left by 2
- Add to PC+4




---
## 3 Datapath Implementations
### Single-Cycle Datapath
> Each instruction completes in **one clock cycle**.

**Advantages:**
- Simple control logic
    

**Disadvantages:**
- Clock cycle must be long enough for the _slowest instruction_
- Impractical for high-performance CPUs
    

### Multi-Cycle Datapath
> Instructions are broken into multiple steps across cycles.

Common stages:
1. IF – Instruction Fetch
2. ID – Instruction Decode & Register Read
3. EX – Execute / Address Calculation
4. MEM – Data Memory Access
5. WB – Write Back
    

**Benefits:**
- Shorter clock period
- Hardware reuse
    


### Pipelined Datapath
> Overlaps execution of multiple instructions to increase throughput.
- Each stage handles a different instruction simultaneously
- Requires additional hardware:
    - Pipeline registers (IF/ID, ID/EX, EX/MEM, MEM/WB)
        

**Challenges:**
- Data hazards
- Control hazards
- Structural hazards
    

(See: [[Hazards, forwarding, and stalls]]) 




---
## 4 Relationship Between Datapath and Control

- Datapath provides the **hardware pathways**
- Control unit provides **control signals**
- Together, they define how instructions execute each cycle
    

Examples of control signals affecting the datapath:
- RegWrite
- MemRead / MemWrite
- ALUSrc
- MemToReg
- Branch



---
# Active Recall
# References
## Textbook
- Chapter 1
	- 1.4
- all of chapter 4