11-24-2025 15:43

Status: 

Tags: [[CS250 Computer Architecture - Class Outline]]

Prev Topic: [[🔴 Control and Task Management]] Next Topic: [[Performance]]

Prev Note: Next Note [[Execution Models and Coordination Parallel Systems]] OR [[Processor Architecture]]
# Parallelism
> running processes at the same time to increase performance
> 
> enabled by PROCESSORS


## 1 Decomposition and Data Dependences
Parallelism is restricted by this

- A computation that depends on a prior result must execute in order
- The **critical path** is the longest chain of dependent operations
- No program can run faster than its critical path
- Most programs contain independent work that can execute in parallel


---
## 2 Granularity of Parallelism
### Fine-Grain Parallelism
- Frequent communication between tasks
- Requires very low latency and high throughput
- Example: instruction-level parallelism (multiple issue)
    

### Coarse-Grain Parallelism
- Infrequent communication
- Common in multiprocessor programs
    

### Embarrassingly Parallel
- Little or no communication
- Ideal for massive parallelism



---
## 1 Levels and Types of parallelism
### Instruction Level Parallelism
> Running instructions in parallel
- Pipelining
- Multiple issue
- Superscalar execution
- Dynamic pipeline scheduling (reordering execution of instructions)
- Speculation

**Issue slots**
> Positions from which instructions may issue in a single clock cycle.

**Multiple issue**
> launching more than one instruction per cycle.
- **Static multiple issue** - decisions made by the compiler
- **Dynamic multiple issue** - decisions make by hardware

**Superscalar Processors**
> Dynamically issue multiple instructions per cycle.



### Data Level Parallelism
> Parallelism achieved by performing the same operation on independent data





---
## 4 Performance and Scalability

### Amdahl’s Law
$$
\text{Speedup}=\dfrac{1}{(1−f)+f/s} 
$$
Where:
- _f_ = fraction of execution time affected
- _s_ = speedup of the improved portion
    

### Scaling

**Strong Scaling**
> Performance improvement without increasing problem size.

**Weak Scaling**
> Performance improvement while increasing problem size proportionally to processor count.


### Bisection Bandwidth
> The bandwidth between two equal halves of a multiprocessor system in the worst case.
- Measures communication capability
- Limits scalability for communication-heavy workloads




---
# Active Recall Questions


# References