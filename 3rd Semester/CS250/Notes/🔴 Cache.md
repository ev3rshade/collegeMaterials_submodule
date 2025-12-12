Opened 03:27

Status: cs250

Tags: [[🟡 Memory]] 

Chapters: 5.3, 5.4

# Cache
> memory from which high-speed retrieval is possible

## 1 Technology | SRAM (Static RAM) (5.2)
> Integrated-circuit memory using **6–8 transistors per bit**. 
- One access port per array is common (though multi-ported SRAM exists).
- Faster but far more expensive than DRAM

### 1.1 Characteristics
- **Volatility:** volatile
- **Access time:** very fast
- **Bandwidth:** high
- **Capacity:** small to moderate
- **Technology:** stable bistable flip-flops; no refresh needed
- **Access granularity:** word-level (defined by ISA)
- **Cost per bit:** high
- Temporal locality + Spatial locality

### 1.2 Usage
#### L1 Cache
(a cache for a cache)
L1 cache, known as the primary cache, can be used as a cache for the L2 cache

#### L2 Cache
(a cache for main memory)
The L2 cache is faster than main memory, but tends to be larger and slower than the L1 cache

#### TLB 
see [[Address Spaces]]






---
## 2 Cache Line
### 2.1 Structure
#### Cache index
> address of a cache line
> a portion of a memory address that directs a CPU or database system to a cache line within the cache

#### Tag
> A field in a table used for a memory hierarchy that contains the address information required to identify whether the associated block in the hierarchy corresponds to a requested word.

#### Valid bit
> A field in the tables of a memory hierarchy that indicates that the associated block in the hierarchy contains valid data.

#### Dirty Bit 
(only for write policies)
> a flag in computer systems, typically a single bit, that indicates a block of memory or data has been modified since it was last saved to storage
#### Data Block
> a fixed piece of memory cache fetches from main memory on a cache miss

#### 2.1.1 Diagram of Cache Line Structure
![[Screenshot 2025-12-12 001730.png]]


### 1.2 Accessing a Cache Line
##### Tag and valid bit access example 5.3.3
--> request to address 00110

| Index | V   | Tag | Data          |
| ----- | --- | --- | ------------- |
| 000   | N   |     |               |
| 001   | Y   | 00  | Memory(00001) |
| 010   | N   |     |               |
| 011   | N   |     |               |
| 100   | Y   | 11  | Memory(11100) |
| 101   | N   |     |               |
| 110   | N   |     |               |
| 111   | Y   | 10  | Memory(10111) |
The request to address 00110two results in a cache miss, so the word at address 00110two is brought into cache block 110two. The lower 3 bits of the address (110) specify the cache block mapping, and the upper 2 bits of the address (00) become the tag.






---
## 3 Cache Organizations
### 3.1 Direct-mapped cache
> A cache structure in which each memory location is mapped to exactly one location in the cache.

#### 3.1.1 Addressing
mapping from memory block --> cache block: 

$$
(\text{Block address}) \text{ modulo } (\text{Number of blocks in the cache})
$$

block # is:
$$
\dfrac{\text{Byte address}}{\text{Bytes per block}}
$$

#### 2.2.2 Diagram of Direct-Mapped Cache Addressing
![[Screenshot 2025-12-10 030156.png]]
Can see low density --> high density mapping

#### 2.2.3 Size of a Direct Mapped Cache
##### Tag Field Sizes
- $m$ = Block offset bits = number of words in block
- $n$ = Index bits = $\log_2({\text{Number of blocks})}$
- byte offset bits = 2

##### Total number of bits in a Direct Mapped Cache
$$
\text{cache size} \times (\text{block size} + \text{tag size} + \text{valid field size})
$$

- $\text{cache size}$ = number of blocks = $2^n$ blocks
- $\text{block size}$ = $2^{m + \text{word size in bits}}$ bits
- $\text{tag size}$ = address size - (index bits - block-offset bits + byte-offset bits) = address size - $n$ - $m$ - 2 bits
- $\text{valid field size} = 1$


### 3.2 Set-associative cache
> A cache that has a fixed number of locations (at least two) where each block can be placed.
> based on SETS of blocks

mapping from memory block --> cache block: 

Block # is:
$$
(\text{Block address}) \text{ modulo } (\text{Number of blocks in the cache} - \text{block number}/\text{location number})
$$


### 3.3 Fully associative cache
> A cache structure in which a block can be placed in any location in the cache.

mapping from memory block --> cache block: 

block # is:
$$
\text{Any of the eight blocks}
$$




### 3.4 Diagrams of Cache Organizations
![[Screenshot 2025-12-10 033003.png]]

Where is a block found?
![[Screenshot 2025-12-10 043929.png]]

How is a block found? 
![[Screenshot 2025-12-10 043938.png]]

### 3.5 Hit and Miss (accessing data)
problems 5.4.5 - 5.4.7 (THIS WILL TEACH YOU)



---
## 4 Hit and Miss Behavior
### 4.2 Cache miss
> A request for data from the cache that cannot be filled because the data are not present in the cache.

Steps taken in the event of a cache miss
1. Send the original PC value to the memory.
2. Instruct main memory to perform a read and wait for the memory to complete its access.
3. Write the cache entry, putting the data from memory in the data portion of the entry, writing the upper bits of the address (from the ALU) into the tag field, and turning the valid bit on.
4. Restart the instruction execution at the first step, which will refetch the instruction, this time finding it in the cache.

#### 4.2.1 Three C's Model
> A cache model in which all cache misses are classified into one of three categories: compulsory misses, capacity misses, and conflict misses
##### Compulsory miss
> (cold-start miss) A cache miss caused by the first access to a block that has never been in the cache.
##### Capacity miss
> A cache miss that occurs because the cache, even with full associativity, cannot contain all the blocks needed to satisfy the request.
##### Conflict miss: 
> (collision miss) A cache miss that occurs in a set-associative or direct-mapped cache when multiple blocks compete for the same set and that are eliminated in a fully associative cache of the same size.


#### 4.2.2 Multilevel Caches
Global miss rate 
> The fraction of references that miss in all levels of a multilevel cache.

Local miss rate 
> The fraction of references to one level of a cache that miss; used in multilevel hierarchies.






---
## 5 Policies

### 5.3 Replacement Policies
#### 5.3.1 Least recently used (LRU)
> A replacement scheme in which the block replaced is the one that has been unused for the longest time.

### 5.2 Write Policies
#### 5.2.1 Write-through
> update both the cache and the next lower level of the memory hierarchy
> to ensuring that data are always consistent between the two

#### 5.2.2 Write-back
> handles writes by updating values only to the block in the cache, then writing the modified block to the lower level of the hierarchy when the block is replaced.

Write buffer
> A queue that holds data while the data are waiting to be written to memory.





---
## 6 Cache Coherence
> in a coherent cache
>- A processor must always read its **own most recent write** to a location if no other processor has written that location inbetween.
  >  
>- A processor must eventually see **another processor’s write** to a location, assuming enough time passes and no intervening writes occur.
>
>- **Writes to the same address must be seen in the same order** by all processors (serialization).

#### Coherence
> Defines _what_ values can be returned by a read.
#### Consistency
> Defines _when_ written values will be returned by a read.
#### Write Serialization
> Method that ensures writes to a location are seen in the same order by all processors.

### Snooping
- most popular cache protocol
- A write invalidate protocol
- Each cache contains a copy of data from a block of physical memory along with a copy of the sharing status of that block. Each cache contains a controller that monitors, or snoops, activity on a shared communication medium to determine if any action is needed to ensure cache coherence.

What it helps with:
Reducing Latency




---
## 7 Consistency

---
## 8 Cache performance

#### Measuring performance
#revise ==check chapter 5.4 for equations for now==



### 8.2 Dependability


#### Improving performance

##### Multilevel cache
> A memory hierarchy with multiple levels of caches, rather than just a cache and main memory.
- First level caches are more concerned about hit time
- Second level caches are more concerned about miss rate
	- the second-level cache contains the desired data, the miss penalty for the first-level cache will be essentially the access time of the second-level cache, which will be much less than the access time of main memory

##### Software optimization via blocking
> reusing data in cache in a program (arrays are an example) (temporal locality)



## Terminology

False sharing
> When two unrelated shared variables are located in the same cache block and the full block is exchanged between processors even though the processors are accessing different variables.

Prefetching 
> A technique in which data blocks needed in the future are brought into the cache early by using special instructions that specify the address of the block. (prediction)

Split cache (5.3)
>A scheme in which a level of the memory hierarchy is composed of two independent caches that operate in parallel with each other, with one handling instructions and one handling data.

Write invalidate protocol
> invalidates copies in other caches on a write. Exclusive access ensures that no other readable or writable copies of an item exist when the write occurs: all other cached copies of the item are invalidated.

# Active Recall

## Textbook
- problems 5.3.5
- problems 5.4.3
- problems 5.4.5 - 5.4.7
# References
## Textbook
Chapter 5
- 5.1-5.4