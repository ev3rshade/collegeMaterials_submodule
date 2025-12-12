11-24-2025 16:14

Status: #cs250

Tags: 

Chapters: 1.3, 4.10
# Compilation

## Optimizations

###  Instruction Level [[Parallelism]]
##### Loop unrolling
> A technique to get more performance from loops that access arrays, in which multiple copies of the loop body are made and instructions from different iterations are scheduled together.

#### Other
Register renaming
> The renaming of registers by the compiler or hardware to remove antidependences.

#### [[Instruction Scheduling]]
> reordering instructions to reduce stall time
## Terminology

Antidependence
> (name dependence) An ordering forced by the reuse of a name, typically a register, rather than by a true dependence that carries a value between two instructions.

Commit unit
> The unit in a dynamic or out-of-order execution pipeline that decides when it is safe to release the result of an operation to programmer-visible registers and memory.

In-order commit
> A commit in which the results of pipelined execution are written to the programmer visible state in the same order that instructions are fetched.

Reservation station
> A buffer within a functional unit that holds the operands and the operation.

Reorder buffer
> The buffer that holds results in a dynamically scheduled processor until it is safe to store the results to memory or a register.
# References