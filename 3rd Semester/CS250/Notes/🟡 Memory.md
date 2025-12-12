10-30-2025 01:14

Status: cs250

Tags: #memoryHierarchy


# Memory
> a place to store values to represent information in the machine

---
## 1 Characteristics of a memory system
### 1.1 Volatility
#### Volatile Memory
> memory that loses data when power is removed
#### Non-volatile Memory
> retains data without power


### 1.2 Access Time / Latency
> How long it takes to retrieve a single piece of data

Fast memory (registers) --> Close to CPUS
Slow memory (disk) --> furthest away


### 1.3 Bandwidth
> How much data can be transferred per second (Bytes / Second)


### 1.4 Capacity
> How much data can be stored (Bytes)
###### Unit - byte
kilo | mega | giga | tera | peta | exa  | zetta | yotta
kibi | mebi | gibi | tebi | pebi | exbi | zebi | yobi

Typically, higher levels of hierarchy have lower capacity


### 1.5 Organization and Addressability (how data is organized and accessed)
#### Word Size
> (see 2. Representing Data) (8-bit, 16-bit, etc.)

#### Block (or line)
> The minimum unit of information that can be either present or not present

#### Addressable Units
> what unit is being used to address data (e.g. byte addressing)


### 1.6 Physical Structure / Technology
> What is the hardware being used

e.g.
Registers
SRAM
DRAM
Flash
Magnetic Disk

(see 3. below for more detail)



### 1.7 Access Method
#### Random Access
- RAM, caches, ROM
#### Sequential access
(not relevant to this course)
#### Read-only vs. Read Write
- ROM
#### Block vs. Byte access
- Reading by large, fixed size chunks or byte by byte



### 1.8 Cost per Bit
Higher-performance memory costs more, driving design by MEMORY HIERARCHY

Registers --> extremely expensive
Cache --> expensive
DRAM --> cheap
SSD -->  cheaper
HDD --> cheapest

### 1.9 Power Consumption (not relevant in cs250)
> different memory types have different power needs







---
## 2 Memory Access
### 2.1 Measures of Memory Access
#### Hit Rate
> The fraction of memory accesses found in a level of the memory hierarchy.

#### Miss Rate
> The fraction of memory accesses not found in a level of the memory hierarchy.

#### Hit Time
> The time required to access a level of the memory hierarchy, including the time needed to determine whether the access is a hit or a miss.

#### Miss penalty:
> The time required to fetch a block into a level of the memory hierarchy from the lower level. Includes time to:
>- access the block
>- transmit block from one level to the other
>- insert block in the level that experienced the miss
>- pass the block to the requestor


---
## 3 Memory Hierarchy
> A structure that uses multiple levels of memories; as the distance from the processor increases, the size of the memories and the access time both increase.

### 3.1 Design of Memory Hierarchy
Temporal Locality
> The locality principle stating that if a data location is referenced then it will tend to be referenced again soon.

Spatial Locality
> The locality principle stating that if a data location is referenced, data locations with nearby addresses will tend to be referenced soon.

The memory hierarchy is built with these two principles in mind


### 3.2 Levels of Memory Hierarchy

-Fastest access-
### Processor 
(hardware [[🔴 Registers]]) 
⬆️⬇️⬆️⬇️⬆️⬇️⬆️⬇️

### [[🔴 Cache]] (5.3)
(hardware: SRAM)
⬆️⬇️⬆️⬇️⬆️⬇️⬆️⬇️

### [[Main memory]]
(hardware: DRAM)
⬆️⬇️⬆️⬇️⬆️⬇️⬆️⬇️

### [[Disk]]
(hardware: Magnetic Disk)

-slowest access-



### 3.3 Diagram of Memory Hierarchy
![[Screenshot 2025-12-11 221557.png]]




### 2.4 External Memory
#### Flash Memory
> A type of **EEPROM (electrically erasable programmable ROM)** used in SSDs, phones, microcontrollers.

#### Characteristics
- **Volatility:** non-volatile
- **Access time:** slower than DRAM, much faster than disk
- **Bandwidth:** high (especially for sequential access)
- **Capacity:** large
- **Density:** high
- **Technology:** floating-gate transistors (charge trapping)
- **Write behavior:**
    - reads = fast
    - writes = slower
    - erases = block-based (entire block must be erased before writing)
    - writes to the same location deteriorate the memory bits 
- **Cost per bit:** more expensive than disk, cheaper than DRAM

#### Usage 
SSDs, firmware storage, embedded systems





---


## 5 Performance

## 6 Error Handling
Error detection code
> A code that enables the detection of an error in data, but not the precise location and, hence, correction of the error.

## Pitfalls and Fallacies #revise
Pitfall: Ignoring memory system behavior when writing programs or when generating code in a compiler.

Pitfall: Forgetting to account for byte addressing or the cache block size in simulating a cache.

Pitfall: Having less set associativity for a shared cache than the number of cores or threads sharing that cache.

Pitfall: Using average memory access time to evaluate the memory hierarchy of an out-of-order processor.

Pitfall: Extending an address space by adding segments on top of an unsegmented address space.


Fallacy: Disk failure rates in the field match their specifications.

Fallacy: Operating systems are the best place to schedule disk accesses.

---
## Circuitry (7.8)
### Basic Memory Circuits
#### Flip-flop
> a memory element for which output is equal to the value of the stored state inside the element and for which the internal state is changed only on a clock edge.
- D flip-flop: A flip-flop with on data input that stores the value of that input signal in the internal memory when the clock edge occurs.
#### Latch
> A memory element in which the output is equal to the value of the stored state inside the element and the state is changed whenever the appropriate inputs change and the clock is asserted.
- S'R' Latch : (active-low SR latch) a **basic memory element** built from **NOR gates**. It stores **one bit** of information and is one of the simplest forms of sequential logic.
### Timing
#### Setup time
> The minimum time that the input to a memory device must be valid before the clock edge
#### Hold Time
> The minimum time during which the input must be valid after the clock edge.


---
## Units / terminology
Fault
> used to mean failure of a component

Synchronous system (7.7)
> A memory system that employs clocks and where data signals are read only when the clock indicates that the signal values are stable.

# References

## Labs
Lab 12

## Textbook
- Chapters 1
	- 1.2
	- 1.4
- Chapter 2
	- 2.3
- Chapter 5
	- 5.1
- Chapter 7
	- 7.7 - 7.9