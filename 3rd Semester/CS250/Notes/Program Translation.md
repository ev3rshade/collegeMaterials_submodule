Opened 20:15

Status: #cs250

Tags:  [[Abstraction]]

# Program Translation
### C program
--> [[Compilation]]
### Assembly language program
--> [[Assembly]]
### Object: Machine language module
\+ Object: Library routine (machine language)
--> [[Linker]]
### Executable: Machine language program
>a functional program in the form of an object file that contains no unresolved references. it can contain symbol tables and debugging information. ("stripped" doesn't contain). relocation information may be included for the loader

--> [[Loader]]
### Memory


## Components of a program
### Program counter
> the register containing the address of the instruction in the program being executed
> -- counts in 4 bytes for LEGv8 (size 32 bit)


# What makes up a program
## Instructions
##### Procedure
> a stored subroutine that performs a specific task based on the parameters with which it is provided

##### Branch-and-link instruction
> an instruction that branches to an address and simultaneously saves the address of the following instruction in a register (LR or X30 in LEGv8)
> -- **Return address** - a link to the calling site that allows a procedure to return to the proper address (`BR LR`)

**Caller** - the program that instigates a procedure and provides necessary parameter values
**Callee** - a procedure that executes a series of stored instructions based on parameters provided by the caller and then returns control to the caller



==memory stuff (might move)==
Registers X0-X7 are used to pass values to a procedure and used to store return values

##### Stack
> A region in memory
> Make room by subtracting
> **stack pointer** - `SP` - the value denoting the most recently allocated address in a stack that shows where registers should be spilled
> Push and pop
- **Procedure frame (activation record)** - segment of the stack containing a procedure's saved registers and local variables
##### Global pointer
> the register that is reserved to point to the static area
##### Frame pointer
> a value denoting the location of the saved registers and local variables for a given procedure

##### Heap

### Libraries
#### Dynamically linked libraries (DLLs)
> library routines that are linked to a program during execution
# References