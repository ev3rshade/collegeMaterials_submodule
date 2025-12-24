Opened 12-13-2025 22:13

Status:

Tags: cs250

Topic: 9

Prev Note: [[9 Parallelism (improving computer execution)]] Next Note: [[SIMD]] OR [[MIMD]] OR [[Special Parallel Architectures- Grid, MISD, and Reliability]]
# Processor Architecture
>the design and structure of a CPU, dictating how it processes instructions and communicates with other components

---
## 1 Processor System Types

### Uniprocessor Systems
> Systems with a single processor.
- No true parallelism
- Concurrency achieved via **interleaving** and context switching

### Multiprocessor Systems
> Systems with two or more processors.
- Enable true parallel execution
- Can execute multiple instruction streams simultaneously
- Common in multicore CPUs and servers




---
## 2 Multiprocessor Organization

### Symmetric Multiprocessors (SMP)
- Identical processors
- Shared memory
- Examples: multicore CPUs, cluster nodes
    

### Asymmetric Multiprocessors
- Different processors with specialized roles





---
## 3 Performance Metric

### Bisection Bandwidth
> Bandwidth between two equal halves of a multiprocessor system in the worst case.
- Measures communication scalability

## Flynn Taxonomy
> classification of parallel systems

### SISD
- Single Instruction, Single Data
- Classic sequential computer
    
### SIMD
- Single Instruction, Multiple Data
- GPUs, vector processors
    
### MISD
- Multiple Instruction, Single Data
- Rare; data pipelining
    
### MIMD
- Multiple Instruction, Multiple Data
- Clusters, multicore systems
    

> Many real systems are hybrids of these categories


# References