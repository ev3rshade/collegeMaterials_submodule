Opened 17:35

Status: #cs250

Tags: [[Assembly]]

# Instruction Sets

Stored program concept - idea that programs are stored on computers alongside data

## Representing on computer
Instructions are made up of a series of fields --> represented in binary
Instruction format --> machine language

### 32 bits is the size of an LEGv8 Instruction

### Fields of an instruction
#### Opcode
> the field that denotes the operation and format of an instruction

Ex: `ADD X1, X4, X3`

| opcode                                  | Rm                     | shamt  | Rn              | Rd                                           |
| --------------------------------------- | ---------------------- | ------ | --------------- | -------------------------------------------- |
| 11 bits                                 | 5 bits                 | 6 bits | 5 bits          | 5 bits                                       |
| Indicates what the instruction performs | Second source register |        | Source register | Indicates the register to receive the result |
| ADD                                     | X3                     | Unused | X4              | X1                                           |

## Instruction Types (TABLE IN 2.2, 2.5)
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


### Encoding of an instruction
==see table 2.10==


### Compiling instructions
[[Instruction Scheduling]]
### Executing instructions
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


## Other instruction sets
### MIPS
### ARMv7 (32-bit) instructions
### x86 instructions
### ARMv8 (64-bit) instruction set

## Terminology
Branch target address
> The address specified in a branch, which becomes the new program counter (PC) if the branch is taken. In the LEGv8 architecture, the branch target is given by the sum of the offset field of the instruction and the address of the branch.

Very Long Instruction Word (VLIW)
> A style of instruction set architecture that launches many operations that are defined to be independent in a single wide instruction, typically with many separate opcode fields.
# References