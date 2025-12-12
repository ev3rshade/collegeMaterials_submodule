Opened 17:35

Status: #cs250

Tags: [[Assembly]]

# Instruction Sets
> the set of commands understood by a given (computer) architecture
> i.e. the fundamental language of a computer

==The instruction set used in this course is [[ARM LEGv8]]==


---
### 1 Characteristics

### 1.1 Instruction Format
- Length
- Number and size of fields
- Encoding scheme

### 1.2 Instruction Types
### One type
#### Arithmetic
#### Data Transfer
> a command that moves data between memory and registers

#### Logical
LSL LSR
AND OR NOT EOR
#### Conditional Branch
> test value, then transfer control to a new address in the program based on the outcome of the value tested


Branch address table (branch table) - a table of addresses of alternative instruction sequences
#### Unconditional Jump

### Another type
#### R type
> uses bits 20:10 for two fields: an operand register (5 bits), and a shift amount (6 bits)
#### I type
> 
#### D type
> uses a constant to indicate the offset from a base address. A D-type instruction has a 9 bit immediate fieldd


## 2 Instruction Representation

### 1.1 Fields of an instruction
#### Opcode
> the field that denotes the operation and format of an instruction

### Encoding of an instruction
==see table 2.10==


### Compiling instructions

## Instruction Execution
######  Stored program concept
> idea that programs are stored on computers alongside data
###### Basic steps
1. fetch from memory using program counter (PC)
2. read one or two registers, using fields of the instruction to select the registers to read.
	1. for the `LDUR` and `CBZ` instructions, we need to read only one register, but most other instructions require reading two registers.
3. ALU - use to execute instruction for one of the following
	1. use ALU for address calculation
	2. use ALU for arithmetic-logic
	3. use ALU for comparisons

![[Screenshot 2025-12-09 132805.png]] #revise 

###### Branching
1. Branch taken:  A branch where the branch condition is satisfied and the program counter (PC) becomes the branch target. All unconditional branches are taken branches.
2. Branch not taken or (untaken branch): A branch where the branch condition is false and the program counter (PC) becomes the address of the instruction that sequentially follows the branch.
![[Screenshot 2025-12-09 135049.png]]

#### [[Pipelining]]
#### [[Parallelism]]
Arithmetic
![[Screenshot 2025-12-09 130702.png]]


## Real World Instruction sets
- MIPS
- ARMv7 (32-bit) instructions
- x86 instructions
- ARMv8 (64-bit) instruction set

## Terminology
Branch target address
> The address specified in a branch, which becomes the new program counter (PC) if the branch is taken. In the LEGv8 architecture, the branch target is given by the sum of the offset field of the instruction and the address of the branch.

Very Long Instruction Word (VLIW)
> A style of instruction set architecture that launches many operations that are defined to be independent in a single wide instruction, typically with many separate opcode fields.
# References

## Textbook
- Chapter 2
	- 2.1