Opened 16:51

Status: 

Tags: [[CS250 Computer Architecture - Class Outline]]

Topic: 0

Prev Topic: [[9 Parallelism (improving computer execution)]] Next Topic:

Prev Note: Next Note:
# Performance
> Metrics that define how efficient a computer system is at completing work. Performance can relate to **speed**, **throughput**, **resource usage**, and **energy efficiency**.

Performance always depends on:

- **The task / workload**
- **The metric being measured** (time, throughput, energy, etc.)
    

---

## 1 Time-Based Metrics
### Response Time / Execution Time
> Total time required for a computer to complete a task from start to finish.

Includes:
- Disk access time
- Memory access time
- I/O activity
- Operating system overhead
- CPU execution time
    

Lower execution time ⇒ **better performance**.

#### CPU Time Breakdown
- **CPU execution time (CPU time):** Time CPU spends computing for the task
- **User CPU time:** Time spent executing the program itself
- **System CPU time:** Time spent in the OS on behalf of the program

#### ==IMPORTANT NOTE==
System performance usually refers to **elapsed (wall-clock) time** on an unloaded system.  
CPU performance usually refers to **user CPU time**.



### Throughput (Bandwidth)
> Number of tasks completed per unit time

- Important for servers, data centers, pipelines
- Increasing throughput does **not necessarily** reduce response time
    




---
## 2 Clocking and Instruction Metrics
### Clock Rate and Clock Cycle
- **Clock rate:** Number of cycles per second (Hz)
- **Clock cycle time (period):** Time per cycle
    

$\text{Clock rate} = \dfrac{1}{\text{Clock cycle time}}$


Example:
- 1 GHz = 1 billion cycles/second
- Clock cycle time = 1 ns


### Instruction Count
> Total number of instructions executed by a program

- Determined by:
    - Algorithm
    - Programming language
    - Compiler
    - Instruction set architecture (ISA)
        

### CPI (Cycles Per Instruction)

> Average number of clock cycles per instruction

- Varies by:
    - Instruction mix
    - Processor implementation
    - Memory system behavior
        

Related metric:
- **IPC (Instructions Per Cycle)**
    - IPC = 1 / CPI
        

---

## The Classic CPU Performance Equation

$$
\text{CPU Time} = \text{Instruction Count} \times \text{CPI} \times \text{Clock Cycle Time}  
$$

or equivalently:

$$
\text{CPU Time} = \frac{\text{Instruction Count} \times \text{CPI}}{\text{Clock Rate}}  
$$

### IMPORTANT OBSERVATION

Improving performance requires improving **at least one** of:

- Instruction count
- CPI
- Clock rate
    

Changing one factor may negatively affect another.





---
## 4 Relative Performance

- Performance is defined as the **inverse of execution time**:
    

$$
\text{Performance} = \frac{1}{\text{Execution Time}}  
$$

If computer X is _n_ times as fast as computer Y:

$$
\frac{\text{Performance}_X}{\text{Performance}_Y} = n  
$$

$$
\frac{\text{Execution Time}_Y}{\text{Execution Time}_X} = n  
$$





---
## 5 Amdahl's Law

> Limits the maximum speedup achievable by improving only part of a system.

$$
\text{Speedup} = \frac{1}{(1 - f) + \frac{f}{s}}
$$

Where:

- _f_ = fraction of execution time affected (parallelizable portion)
- _s_ = speedup of the improved portion
    

### Scaling Models

#### Strong Scaling
> Speedup achieved **without increasing problem size** as processors increase

#### Weak Scaling
> Speedup achieved **while increasing problem size proportionally** to processor count

Notes:
- Load imbalance limits achievable speedup
- Serial portions dominate at scale
    




---
## 6 Energy and Power Metrics (The Power Wall)

### Power vs Energy

- **Power (Watts):** Rate of energy consumption (Joules/second)
- **Energy (Joules):** Total energy consumed
    

> Energy is often the more meaningful metric, especially for mobile devices and data centers.

### The Power Wall

- Clock rates increased rapidly until ~2004
- Power and heat dissipation became unsustainable

- Resulted in:
    - Flattened clock rates
    - Shift to multicore processors
    - Emphasis on energy efficiency
        

---

## 7 Benchmark-Based Performance Metrics

### Workload
> A set of programs with defined frequencies used to evaluate performance

### Benchmarks
> Programs chosen to measure and compare performance

#### ==SPEC Benchmarks==
> **standardized, representative, and carefully designed to avoid common measurement pitfalls**

- **SPEC CPU (CINT / CFP):** Processor performance
- **SPECratio:** Reference time / measured execution time
    
    - Higher SPECratio ⇒ better performance
        
- **Geometric mean** used to summarize results
    

#### Power Benchmarks

- **SPECpower:** Measures performance per watt
- Metric: overall ssj_ops per watt





---
## 8 Key Takeaways

- ==**Time is the most reliable measure of performance** MEASURED BY THE SPEC BENCHMARKS==
    
- No single metric tells the whole story
    
- Performance, power, and energy are deeply intertwined
    
- Modern systems prioritize parallelism and efficiency over clock speed




---

# References
## Textbook
- Chapter 1 
	- 1.2
	- 1.6-1.8