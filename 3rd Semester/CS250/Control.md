Opened 23:02

Status: #cs250

Tags:

# Control
## Control Unit
> uses bits and different signals to indicate the operations an instruction will perform
#### ALU Control
1. The ALU's four control inputs (the thick wire below the ALU) perform the functions shown.
2. An instruction's opcode defines the needed ALU function. The ALU control converts the 2-bit ALUOp signal (derived from opcode) and 11-bit opcode to the 4 ALU control inputs.
3. For a load or store instruction, the ALU should perform an add to determine the memory address (by adding a base address and offset).
4. For a compare and branch on equal 0, a pass input b is performed to test for zero.
5. For all R-type instructions, ALUOp is 10. The 11-bit opcode field in the instruction determines whether to perform an add, subtract, AND, etc.
![[Screenshot 2025-12-09 224648.png]]
==do questions in 4.4.2 and 4.4.3 to test knowledge==
#### Main control unit
> uses 2 bit signals as control inputs to the ALU control

Datapath with control: a simple example 4.4.5
![[Screenshot 2025-12-09 225524.png]]
==watch animation 4.4.6==
##### Signals
![[Screenshot 2025-12-09 225728.png]]
![[Screenshot 2025-12-09 225741.png]]
Example: `LDUR`

| Signal | Branch                   | MemRead                | MemToReg                      | ALUSrc                                      | RegWrite             |
| ------ | ------------------------ | ---------------------- | ----------------------------- | ------------------------------------------- | -------------------- |
| Bit    | 0                        | 1                      | 1                             | 1                                           | 1                    |
| Reason | not a branch instruction | reads from data memory | data memory flows to register | ALU computes memory address for instruction | writes into register |
==walk through 4.4.8 to understand==


# References