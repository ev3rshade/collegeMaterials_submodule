11-24-2025 15:43

Status: #cs250

Tags: [[Data Dependency]] [[Performance]]

Chapters: 1.2
# Parallelism
> running processes at the same time to increase performance

## Types of parallelism
### Task-level prarallelism
> (Process-level parallelism) Utilizing multiple processors by running independent programs simultaneously.


### Amdahl's Law
$$
\text{Speed-up } = \dfrac{1}{(1-\text{Fraction time affected}) + \frac{\text{Fraction time affected}}{\text{Amount of improvement}}}
$$
#### Scaling
##### Strong Scaling
> speed-up achieved on a multiprocessor without increasing the size of the prblm

##### Weak Scaling
> speed-up achieved on a multiprocessor while increasing the size of the prblm proportionally to the increase in the number of processors

Notes: Balancing the load on slower and faster processors to achieve faster execution time is important, the load is not always even

### Data Level Parallelism
> Parallelism achieved by performing the same operation on independent data


### Instruction Level Parallelism
> Running instructions in parallel

Issue slots
> The positions from which instructions could issue in a given clock cycle; by analogy, these correspond to positions at the starting blocks for a sprint.

#### Multiple issue
> A scheme whereby multiple instructions are launched in one clock cycle.

###### Static multiple issue
> An approach to implementing a multiple-issue processor where many decisions are made by the compiler before execution.

Issue packet
The set of instructions that issues together in one clock cycle; the packet may be determined statically by the compiler or dynamically by the processor.

###### Dynamic multiple issue
> An approach to implementing a multiple-issue processor where many decisions are made during execution by the processor.

Superscalar
> An advanced pipelining technique that enables the processor to execute more than one instruction per clock cycle by selecting them during execution.

Dynamic pipeline scheduling [[Instruction Scheduling]]
> Hardware support for reordering the order of instruction execution to avoid stalls.

Speculation
> An approach whereby the compiler or processor guesses the outcome of an instruction to remove it as a dependence in executing other instructions.



## Multithreading
### Hardware Multithreading
> Increasing utilization of a processor by switching to another thread when one thread is stalled.

**Thread**: A thread includes the program counter, the register state, and the stack. It is a lightweight process; whereas threads commonly share a single address space, processes don't.

**Process**: A process includes one or more threads, the address space, and the operating system state. Hence, a process switch usually invokes the operating system, but not a thread switch.

**Fine-grained multithreading**: A version of hardware multithreading that implies switching between threads after every instruction.

**Simultaneous multithreading (SMT**): A version of multithreading that lowers the cost of multithreading by utilizing the resources needed for multiple issue, dynamically scheduled microarchitecture.

![[Screenshot 2025-12-04 181429.png]]

## Parallelism on Processors
##### Uniform memory access (UMA)
> A multiprocessor in which latency to any word in main memory is about the same no matter which processor requests the access.
##### Nonuniform memory access (NUMA)
> A type of single address space multiprocessor in which some memory accesses are much faster than others depending on which processor asks for which word.


#### Single Instruction Stream (SISD)
> done on a uniprocessor
#### Multiple instruction streams (MIMD)
> done on a multiprocessor


##### Single program, Multiple Data Streams (SPMD)
> The conventional MIMD programming model, where a single program runs across all processors

##### Single Instruction Stream, Multiple Data Streams (SIMD)
> The same instruction is applied to many data streams, as in a vector processor
###### Vector architecture [[Pipelining]]
> 1. collect data elements from memory
> 2. put them in order into a large set of registers
> 3. operate on them sequentially in registers using **pipelined execution units**
> 4. write the results back to memory
> 5. A key feature of vector architectures is therefore a set of vector registers

LEGv8 Code for DAXPY
```
LDURD D0,[X28,a] // load scalar a 
ADDI X0,X19,512 // upper bound of what to load 
LDURD D2,[X19,#0] // load x(i) 
FMULD D2,D2,D0 // a x x(i) 
LDURD D4,[X20,#0] // load y(i) 
FADDD D4,D4,D2 // a x x(i) + y(i) 
STURD D4,[X20,#0] // store into y(i) 
ADDI X19,X19,#8 // increment index to x 
ADDI X20,X20,#8 // increment index to y 
CMPB X0,X19 // compute bound B.NE loop // check if done
```
Vector LEGv8 Code for DAXPY
```
LDURD D0,[x28,a] // load scalar a 
LDURDV V1,[X19,#0] // load vector x 
FMULDVS V2,V1,D0 // vector-scalar multiply 
LDURDV V3,[X20,#0] // load vector y 
FADDDV V4,V2,V3 // add y to product 
STURDV V4,[X20,#0] // store the result
```

Pipelining hazards are applicable here!!! (FADDD must wait for FMULD, STURD must wait for FADDD, FADDD and FMULD must wait on LDURD)

Vector vs Scalar 6.3 #revise

Vector vs Multimedia extensions #revise

Vector lane
> One or more vector functional units and a portion of the vector register file. Inspired by lanes on highways that increase traffic speed, multiple lanes execute vector operations simultaneously.


## Terminology

Cluster
> A set of computers connected over a local area network that function as a single large multiprocessor.

Multicore microprocessor
> A microprocessor containing multiple processors ("cores") in a single integrated circuit. Virtually all microprocessors today in desktops and servers are multicore.

Parallel processing program
> A single program that runs on multiple processors simultaneously.

Shared memory multiprocessor (SMP)
> A parallel processor with a single physical address space.

Synchronization
> The process of coordinating the behavior of two or more processes, which may be running on different processors.
 
Lock
> A synchronization device that allows access to data to only one processor at a time.

# References