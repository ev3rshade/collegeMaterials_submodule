10-30-2025 01:14

Status: #cs250

Tags: 

Chapters: 1.2, 1.4, 2.3, all of chapter 5
# Memory
> a place to store values to represent information in the machine

## Characteristics of memory
1. Alignment restriction
2. Volatile/nonvolatile

## Locality (5.1)
#### Temporal Locality
> The locality principle stating that if a data location is referenced then it will tend to be referenced again soon.
#### Spatial Locality
> The locality principle stating that if a data location is referenced, data locations with nearby addresses will tend to be referenced soon.



## Memory Hierarchy (5.1)
> A structure that uses multiple levels of memories; as the distance from the processor increases, the size of the memories and the access time both increase.

![[Screenshot 2025-11-04 021254.png]]
### Processor
↑↓

Fastest access

---
### [[Cache]] (5.3)
(hardware: SRAM)
↑↓
### Main memory 
(hardware: DRAM)
↑↓
### Disk 
(hardware: Magnetic Disk)

---
Slowest access


## Pitfalls and Fallacies #revise
Pitfall: Ignoring memory system behavior when writing programs or when generating code in a compiler.

Pitfall: Forgetting to account for byte addressing or the cache block size in simulating a cache.

Pitfall: Having less set associativity for a shared cache than the number of cores or threads sharing that cache.

Pitfall: Using average memory access time to evaluate the memory hierarchy of an out-of-order processor.

Pitfall: Extending an address space by adding segments on top of an unsegmented address space.


Fallacy: Disk failure rates in the field match their specifications.

Fallacy: Operating systems are the best place to schedule disk accesses.
## Units / terminology

Block (or line) (5.1)
> the minimum unit of information that can be either present or not present in a cache

Fault
> used to mean failure of a component

Hit Rate (5.1)
> The fraction of memory accesses found in a level of the memory hierarchy

Miss rate (5.1)
> The fraction of memory accesses not found in a level of the memory hierarchy

Hamming distance
> the number of bits that differ between two bit patterns

Hit time (5.1)
>The time required to access a level of the memory hierarchy, including the time needed to determine whether the access is a hit or a miss

Miss penalty (5.1)
> The time required to fetch a block into a level of the memory hierarchy from the lower level, including the time to access the block, transmit it from one level to the other, insert it in the level that experienced the miss, and then pass the block to the requestor

Tag (5.3)
> A field in a table used for a memory hierarchy that contains the address information required to identify whether the associated block in the hierarchy corresponds to a requested word.

Valid bit (5.3)
> A field in the tables of a memory hierarchy that indicates that the associated block in the hierarchy contains valid data.
# References
Lab 12