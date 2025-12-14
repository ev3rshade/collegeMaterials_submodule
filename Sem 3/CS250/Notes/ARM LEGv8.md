10-28-2025 23:17

Status: 

Tags: cs250

Topic: 5

Prev Note: [[Assembly]] Next Note: [[3 Programs]]

# LEGv8
> an assembly language. a simplified subset of the [ARMv8 assembly language](https://www.google.com/search?q=ARMv8+assembly+language&rlz=1C1CHBF_enUS1120US1120&oq=is+legv8+assembly&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTINCAEQABiGAxiABBiKBTIKCAIQABiABBiiBDIKCAMQABiABBiiBDIKCAQQABiABBiiBDIKCAUQABiABBiiBNIBCDM3ODdqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8&mstk=AUtExfCB6IV_hxiwdvMW7FgfFbmmxEVevUbBM3cWDZ6gc-W6kITHyky3OARkNtGsP1kDBwek-Vgi9cvwckerUrpa39AKXi4LVDVMP5PdUWF0AzIG_9EXIFmG8wCTPbWM8ArvW6cN1TP15SqkWrWcTbsxCCSlbAuSeDusIrVqk8pSgVFcyMs&csui=3&ved=2ahUKEwillLGdoJuRAxWwmokEHVZeLFEQgK4QegQIARAC) used for educational purposes

## 1 Instruction Format
### Length (size)
32 bit

### Field Size
- **Opcode** - 11 bits
- **Registers** - 5 bits
- **shamt** - 6 bits


Ex: `ADD X1, X4, X3`

| opcode                                  | Rm                     | shamt  | Rn              | Rd                                           |
| --------------------------------------- | ---------------------- | ------ | --------------- | -------------------------------------------- |
| 11 bits                                 | 5 bits                 | 6 bits | 5 bits          | 5 bits                                       |
| Indicates what the instruction performs | Second source register |        | Source register | Indicates the register to receive the result |
| ADD                                     | X3                     | Unused | X4              | X1                                           |



### Syntax
- One operation, three parameters
### Memory access
Registers
- 32 Registers
- X0 - X30 and XZR (XZR is an example of [[Common Case Fast]])

Memory words
- $2^{62}$
- Only accessed by data transfer instructions
#### Datapath
- has a 64-bit data path in the processor circuitry

## Implementation (datapath)
Instructions that form a basic implementation
1. Memory reference instructions (LDUR, STUR)
2. Arithmetic-logical instructions (ADD, SUB, AND, ORR)
3. Instructions *compare and branch on zero* (CBZ) and *branch* (b)

Steps to execute the implementation
4. Send the program counter to the mem that contains the code and fetch the instruction from that memory
5. Read one or two registers, using fields of the instruction to select the registers to read. 
	1. For LDUR and CBZ 1 register
	2. For other instructions 2 registers



---
## 2 Instruction types (TABLE IN 2.2, 2.5)

### Arithmetic
| Operation | Instruction Forms              | Example                                | Meaning                          | Notes                                                           |
| --------- | ------------------------------ | -------------------------------------- | -------------------------------- | --------------------------------------------------------------- |
| Add       | `ADD`, `ADDI`, `ADDS`, `ADDIS` | `ADD X1, X2, X3`<br>`ADDI X1, X2, #20` | `X1 = X2 + X3`<br>`X1 = X2 + 20` | Immediate forms use constants; `S` versions set condition flags |
| Subtract  | `SUB`, `SUBI`, `SUBS`, `SUBIS` | `SUB X1, X2, X3`<br>`SUBI X1, X2, #20` | `X1 = X2 - X3`<br>`X1 = X2 - 20` | Immediate forms use constants; `S` versions set condition flags |
### Data Transfer
|Instruction|Example|Meaning|Comments|
|---|---|---|---|
|Load register|`LDUR X1, [X2, #40]`|`X1 = Memory[X2 + 40]`|Doubleword memory → register|
|Store register|`STUR X1, [X2, #40]`|`Memory[X2 + 40] = X1`|Doubleword register → memory|
|Load signed word|`LDURSW X1, [X2, #40]`|`X1 = Memory[X2 + 40]`|Word memory → register|
|Store word|`STURW X1, [X2, #40]`|`Memory[X2 + 40] = X1`|Word register → memory|
|Load halfword|`LDURH X1, [X2, #40]`|`X1 = Memory[X2 + 40]`|Halfword memory → register|
|Store halfword|`STURH X1, [X2, #40]`|`Memory[X2 + 40] = X1`|Halfword register → memory|
|Load byte|`LDURB X1, [X2, #40]`|`X1 = Memory[X2 + 40]`|Byte memory → register|
|Store byte|`STURB X1, [X2, #40]`|`Memory[X2 + 40] = X1`|Byte register → memory|
|Load exclusive|`LDXR X1, [X2]`|`X1 = Memory[X2]`|1st half of atomic swap|
|Store exclusive|`STXR X1, X3, [X2]`|`Memory[X2] = X1``X3 = 0 or 1`|2nd half of atomic swap|
|Move wide (zero)|`MOVZ X1, 20, LSL 16`|`X1 = 20 × 2^16`|Load 16-bit constant, zero rest|
|Move wide (keep)|`MOVK X1, 20, LSL 16`|`X1 = 20 × 2^16`|Load 16-bit constant, keep rest|
### Logical
|Operation|Instruction|Example|Meaning|Notes|
|---|---|---|---|---|
|AND|`AND`|`AND X1, X2, X3`|`X1 = X2 & X3`|Bitwise AND|
|OR|`ORR`|`ORR X1, X2, X3`|`X1 = X2 \| X3`|Bitwise OR|
|XOR|`EOR`|`EOR X1, X2, X3`|`X1 = X2 ^ X3`|Bitwise XOR|
|AND immediate|`ANDI`|`ANDI X1, X2, #20`|`X1 = X2 & 20`|Register with constant|
|OR immediate|`ORRI`|`ORRI X1, X2, #20`|`X1 = X2 \| 20`|Register with constant|
|XOR immediate|`EORI`|`EORI X1, X2, #20`|`X1 = X2 ^ 20`|Register with constant|
|Logical shift left|`LSL`|`LSL X1, X2, #10`|`X1 = X2 << 10`|Shift left|
|Logical shift right|`LSR`|`LSR X1, X2, #10`|`X1 = X2 >> 10`|Shift right|
### Conditional Branch
|Instruction|Example|Meaning|Comments|
|---|---|---|---|
|Compare & branch if zero|`CBZ X1, #25`|If `X1 == 0`, branch|PC-relative|
|Compare & branch if not zero|`CBNZ X1, #25`|If `X1 != 0`, branch|PC-relative|
|Conditional branch|`B.cond #25`|Branch if condition true|Uses condition flags|
### Unconditional Branch
|Instruction|Example|Meaning|Comments|
|---|---|---|---|
|Branch|`B #2500`|Jump to target address|PC-relative|
|Branch to register|`BR X30`|Jump to address in register|Used for returns, switches|
|Branch with link|`BL #2500`|`X30 = PC + 4`, then branch|Procedure call|



# References
## Textbook
- Chapter 2 (all of it)