Opened 01:48

Status: #cs250

Tags: [[Datapath]]

Chapters: 4.9

# Exceptions
>An unscheduled event that disrupts program execution; used to detect overflow
>
>**Interrupt:** An exception that comes from outside of the processor. (Some architectures use the term _interrupt_ for all exceptions.)

## Types
![[Pasted image 20251210014959.png]]
## Floating Point Arithmetic (3.5, 4.9)
Floating point exceptions: see [[IEEE Floating Point System]] (separate note not in repository)

## [[Pipelining]]
Exceptions are treated as just another hazard
##### Out-of-order execution
> A situation in pipelined execution when an instruction blocked from executing does not cause the following instructions to wait.

## Page Fault Exceptions
Handled by OS
1. Look up the page table entry using the virtual address and find the location of the referenced page in secondary memory.
2. Choose a physical page to replace; if the chosen page is dirty, it must be written out to secondary memory before we can bring a new virtual page into this physical page.
3. Start a read to bring the referenced page from secondary memory into the chosen physical page.

## Terminology
Vectored interrupt
> An interrupt for which the address to which control is transferred is determined by the cause of the exception.

Imprecise Interrupt
> (Imprecise exception) Interrupts or exceptions in pipelined computers that are not associated with the exact instruction that was the cause of the interrupt or exception.

Precise interrupt 
> (precise exception) An interrupt or exception that is always associated with the correct instruction in pipelined computers.

Restartable instruction
> An instruction that can resume execution after an exception is resolved without the exception's affecting the result of the instruction.

Exception enable
> (interrupt enable) A signal or action that controls whether the process responds to an exception or not; necessary for preventing the occurrence of exceptions during intervals before the processor has safely saved the state needed to restart.
# References