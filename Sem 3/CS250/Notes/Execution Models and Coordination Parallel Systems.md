Opened 12-13-2025 22:31

Status:

Tags: cs250

Topic: 9

Prev Note: [[Parallelism]] Next Note: 

# Execution Models and Coordination Parallel Systems

## 1 Multithreading

### Threads vs Processes
**Thread**
- Program counter, registers, stack  
- Shares address space with other threads
    

**Process**
- One or more threads
- Own address space and OS state

### Hardware Multithreading
> Improving processor utilization by switching threads when one is stalled.

- **Fine-grained multithreading** – switch threads every instruction
- **Simultaneous Multithreading (SMT)** – issue instructions from multiple threads in one cycle

![[Screenshot 2025-12-04 181429.png]]


## 2 Parallel Programming Models

### Shared Memory Model
- All processors share a single address space
- Requires synchronization mechanisms

**Synchronization**
> Coordinating execution of concurrent processes or threads.

**Lock**
> Ensures mutual exclusion to shared data.


### Message Passing Model
> Processors communicate by explicitly sending and receiving messages.

- Common in systems with private or distributed memory
- No shared address space required
    

**Send Message Routine**
> Transmits a message to another processor.

**Receive Message Routine**
> Accepts a message from another processor.



---
## 3 Memory Architectures for Parallel Systems

### Uniform Memory Access (UMA)
> Equal memory access latency for all processors.

### Nonuniform Memory Access (NUMA)
> Memory access time depends on processor location.


# Active Recall

# References