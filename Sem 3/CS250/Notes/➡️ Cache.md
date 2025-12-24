Opened 03:27

Status: 

Tags: cs250

Topic: [[➡️ Memory]]

Prev Note:  Next note: 

Chapters: 5.3, 5.4

# Cache
> memory from which high-speed retrieval is possible

---

## 1 Technology | SRAM (Static RAM) (5.2)
> Integrated-circuit memory using **6–8 transistors per bit**.

- One access port per array is common (though multi-ported SRAM exists)
- Faster but far more expensive than DRAM
    

### 1.1 Characteristics
- **Volatility:** volatile
- **Access time:** very fast
- **Bandwidth:** high
- **Capacity:** small to moderate
- **Technology:** stable bistable flip-flops; no refresh needed
- **Access granularity:** word-level (defined by ISA)
- **Cost per bit:** high
- Exploits **temporal locality** and **spatial locality**
    

### 1.2 Usage
#### L1 Cache
> (a cache for a cache)  
> L1 cache, known as the primary cache, can be used  as a cache for the L2 cache.

#### L2 Cache

>(a cache for main memory)  
>The L2 cache is faster than main memory, but tends to be larger and slower than the L1 cache.

#### Split Cache
> A scheme in which a cache level is divided into two independent caches.
- Instruction cache (I-cache)
- Data cache (D-cache)
    

Allows parallel access to instructions and data.

#### TLB

see [[🟡 Address Spaces]]

---

## 2 Cache Line 
> entry in a cache

### 2.1 Structure

#### Cache index
> a portion of a memory address that selects a cache line or set
#### Tag
> A field that identifies which memory block is stored in the cache line.
#### Valid bit
> Indicates whether the cache line contains valid data.

#### Dirty Bit
(only for write-back policies)
> Indicates the cache block has been modified since being loaded.

#### Data Block
> a fixed-size chunk of memory brought into cache on a cache miss

#### 2.1.1 Diagram of Cache Line Structure
![[Screenshot 2025-12-12 001730.png]]

### 2.2 Accessing a Cache Line
##### Tag and valid bit access example (5.3.3)

--> request to address 00110₂

|Index|V|Tag|Data|
|---|---|---|---|
|000|N|||
|001|Y|00|Memory(00001)|
|010|N|||
|011|N|||
|100|Y|11|Memory(11100)|
|101|N|||
|110|N|||
|111|Y|10|Memory(10111)|

The request results in a **cache miss**, so the word at address 00110₂ is brought into cache block 110₂.
- Lower bits (110) → cache index
- Upper bits (00) → tag
    

---

## 3 Cache Organizations

### 3.1 Direct-mapped cache
> A cache structure in which each memory block maps to exactly one cache location.

#### 3.1.1 Addressing
mapping from memory block → cache block:

$$  
(\text{Block address}) \bmod (\text{Number of cache blocks})  
$$

block number:  
$$  
\frac{\text{Byte address}}{\text{Bytes per block}}  
$$

#### 3.1.2 Diagram of Direct-Mapped Cache Addressing

![[Screenshot 2025-12-10 030156.png]]

#### 3.1.3 Size of a Direct-Mapped Cache

##### Tag Field Sizes
- $m$ = block offset bits
- $n$ = index bits = $\log_2$(number of cache blocks)
- byte offset bits = 2
    

##### Total number of bits

$$  
2^n \times (\text{block size} + \text{tag size} + 1)  
$$

- tag size = address size − (n + m + 2)

### 3.2 Set-associative cache

> A cache where each set contains multiple blocks
- Reduces conflict misses compared to direct-mapped caches

mapping:  
$$  
(\text{Block address}) \bmod (\text{Number of sets})  
$$
### 3.3 Fully associative cache

> A cache where a block can be placed anywhere.
- Eliminates conflict misses
- Requires associative search hardware
    

### 3.4 Comparison of Cache Organizations

|Lower Latency|Direct mapped|Set associative|Fully associative|Higher Latency|
|---|---|---|---|---|
|More misses||||Fewer misses|

#### Cache Organization Visual

![[Screenshot 2025-12-10 033003.png]]

---

## 4 Hit and Miss Behavior

### 4.1 Cache hit
> Requested data is found in the cache.

### 4.2 Cache miss
> Requested data is not found in the cache.

Steps on a miss:
1. Send address to memory
2. Read block from lower level
3. Update cache (data, tag, valid bit) 
4. Restart instruction

#### 4.2.1 Three C’s Model
> Classifies cache misses.
##### 1 Compulsory miss
> First access to a block.
##### 2 Capacity miss
> Cache too small to hold working set.
##### 3 Conflict miss
> Multiple blocks compete for same set.



#### 4.2.2 Multilevel Caches

Global miss rate
> Fraction of references that miss in all cache levels.

Local miss rate
> Fraction of references that miss at a given level.

---

## 5 Policies

### 5.1 Replacement Policies

#### Least Recently Used (LRU)
> Replaces block unused for the longest time.
- Costly beyond 2–4 way associativity
    

#### Random
> Randomly selects a block to replace.

### 5.2 Write Policies

#### Write-through
> Writes update cache and next memory level.

#### Write-back
> Writes update cache only; memory updated on eviction.

**Write buffer**
> Queue holding data waiting to be written to memory.

### 5.3 Prefetching
> Bringing blocks into cache before they are requested.
- Hardware prefetching: automatic pattern detection
- Software prefetching: explicit instructions

Goal:
- Reduce miss penalty
- Hide memory latency

Tradeoff:
- Incorrect prefetching wastes bandwidth





---

## 6 Coherence and Consistency

### 6.1 Cache Coherence and Data Invalidation
> Ensures all caches see a consistent value for a single memory location.

Defines **what** value can be returned.

#### Data Invalidation
> the process of marking or removing outdated data from a cache (like a web cache or memory cache) to ensure applications use fresh, accurate information from the source, balancing performance with data consistency

### 6.2 Cache Consistency
> Defines ordering of memory operations across locations.

Defines **when** values can be read.

### 6.3 Qualities of a Coherent Cache
1 Program order preservation
	1. A processor reads its own most recent write 
2 Write propagation
	2. Writes eventually visible to other processors
3 **Write serialization**
> Ensures consistent ordering of writes


Migration
> Moving data closer to the accessing processor.

Replication
> Multiple caches hold read-only copies.

### 6.4 False Sharing
> When unrelated variables share the same cache block, causing unnecessary invalidations.

### 6.5 Cache Protocols
> Rules that enforce coherence.

#### 6.5.1 Snooping
- Most common protocol
- Write invalidate protocol
- Caches monitor shared bus activity

#### 6.5.2 Write invalidate protocol
> Invalidates other cached copies on a write.






---
## 7 Addressing in Caches

#### Physically addressed cache
> Cache indexed by physical addresses.

#### Virtually addressed cache
> Cache indexed by virtual addresses.

---

## 8 Cache Performance
### 8.1 Measuring performance
Average Memory Access Time (AMAT)
> Hit time + (Miss rate × Miss penalty)

### 8.2 Improving performance
#### Multilevel caches
- Upper levels optimized for hit time
- Lower levels optimized for miss rate
    

#### Software blocking
> Reusing data in cache to exploit locality.

### 8.3 Changing Cache Design Parameters
![[Screenshot 2025-12-12 212907.png]]





---
# Active Recall
## Textbook
- problems 5.3.5
- problems 5.4.3
- problems 5.4.5 – 5.4.7
    

---

# References

## Labs
[[CS250 Lab12 Cache and Memory.pdf]]

## Textbook

Chapter 5
- 5.1–5.4
- 5.7–5.8