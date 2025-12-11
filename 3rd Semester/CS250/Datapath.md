10-30-2025 01:10

Status: #cs250

Tags: #revise

Chapters: 1.4, all of chapter 4

# Datapath
> a unit used to operate on or hold data within a processor. In the LEGv8 implementation includes: instruction and data memories, the register file, the ALU, and adders 
> i.e. path of data flow

## Components
Registers [[Memory Hardware]]
- Program counter (PC)
- Register file
ALU [[Circuitry]]
Addressing

a simple example
![[2 Source Material/College Materials/3rd Semester/CS250/attachments/Screenshot 2025-12-09 135243.png]]

## Implementation
Various implementations
##### Units needed to implement R-format ALU operations
1. the register file
2. ALU.
##### The four units needed to implement loads and stores
1. register file
2. ALU
3. data memory unit
4. and sign extension unit
5. (additional) Wires/muxes
##### The five units needed for a branch
1. ALU - evaluates branch condition
2. adder - computes branch target address (sign extending, then shifting left by 2)
3. The remaining datapath portion for fetching instructions and incrementing the program counter. Nearly the full LEGv8 datapath is now shown.
	1. Program counter
	2. adder
	3. mux

#### Single cycle implementation
> (single clock implementation) an implementation which an instruction is executed in one clock cycle. it is too slow to be practical

#### Multicycle Implementation (4.6)
> 5 stage instruction execution (see [[Pipelining]])
> 1. IF: Instruction fetch
> 2. ID: Instruction decode and register file read
> 3. EX: Execution or address calculation
> 4. MEM: Data memory access
> 5. WB: Write back
> IF to ID; ID to EX; EX to MEM; MEM to WB
![[Screenshot 2025-12-10 013110.png]]
## Terminology
Datapath element
> A unit used to operate on or hold data within a processor. In the LEGv8 implementation, the datapath elements include the instruction and data memories, the register file, the ALU, and adders.



## Circuirty

## **6. Memory & Datapath Components**

### **6.1 Clock**

Controls timing, synchronization, and sequencing of state elements.

### **6.2 Memory Components**

- **Instruction memory**
    
- **Data memory**
    
- **Registers**
    
- **Program Counter (PC)** — holds instruction address
    

_(Your “forgot word memory” might be **data memory** or **main memory** — let me know and I’ll fill it in.)_

### **6.3 Datapath Elements**

> Units that store or operate on data within a processor.  
> Includes:

- Register file
    
- ALU
    
- Instruction memory
    
- Data memory
    
- Adders
    
- Multiplexors
# References
