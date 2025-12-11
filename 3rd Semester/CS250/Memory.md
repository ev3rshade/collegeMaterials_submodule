10-30-2025 01:14

Status: cs250

Tags: #memoryHierarchy

Chapters: 1.2, 1.4, 2.3, all of chapter 5, 7.8


# Memory
> a place to store values to represent information in the machine

---
## 1. Characteristics of a memory system
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
## 2. Memory Hierarchy (5.1)
> A structure that uses multiple levels of memories; as the distance from the processor increases, the size of the memories and the access time both increase.

![[Screenshot 2025-11-04 021254.png]]

## 3. Levels of the Memory Hierarchy ==LAST HERE==

-Fastest access-
### Processor ([[Registers]]) 
↑↓
### [[Cache]] (5.3)
(hardware: SRAM)
↑↓
### [[Main memory]]
(hardware: DRAM)
↑↓
### [[Disk]]
(hardware: Magnetic Disk)

-slowest access-


## 4. Hardware (Technology)

### 4.1 Registers
> A **register file** is a small, fast set of state elements inside the CPU.  
> accessed using register numbers (IDs) and supply operands for instructions.

#### Characteristics
- **Volatility:** volatile
- **Access time:** fastest in entire system (single cycle or sub-cycle)
- **Bandwidth:** extremely high (multiple read/write ports)
- **Capacity:** very small (tens to low hundreds of bytes)
- **Technology:** implemented using **SRAM-like flip-flops**
- **Access granularity:** word-level (defined by ISA)
- **Cost per bit:** highest of all memory types

#### Location 
inside CPU
#### Usage
holding operands, results, state, temporary values, memory access
##### Memory access
Base registers
> register used for address computation (base + offset)
    
Destination register
> register that receives results of an instruction

#### Related registers
##### Program Counter (PC)
> register that holds the address of the next instruction




### 4.2 SRAM (Static RAM) (5.2)
> Integrated-circuit memory using **6–8 transistors per bit**. 

- One access port per array is common (though multi-ported SRAM exists).
- Faster but far more expensive than DRAM.
#### Characteristics
- **Volatility:** volatile
- **Access time:** very fast (ns-scale)
- **Bandwidth:** high
- **Capacity:** small to moderate
- **Density:** low (many transistors per bit)
- **Technology:** stable bistable flip-flops; no refresh needed
- **Cost per bit:** high
    
#### Usage
L1/L2/L3 caches, register files




### 4.3 DRAM (5.2)
> Main memory technology using **1 transistor + capacitor per bit** which requires periodic **refresh**.

Characteristics

- **Volatility:** volatile
- **Access time:** slower than SRAM
- **Bandwidth:** high (burst transfers)
- **Capacity:** large
- **Density:** high
- **Technology:** stored as charge in capacitors; must refresh thousands of times per second
- **Cost per bit:** lower than SRAM

#### Usage
main memory (RAM)
    
#### Organization
- **Banks** → contain **rows**, each storing many bits
- Access occurs in **bursts** per clock edge
- Row activation cost dominates latency
![[Screenshot 2025-12-10 025555.png]]



### 4.4 Disk Memory
> A **mechanical**, magnetic storage device. Non-volatile and extremely high capacity.

#### Characteristics
- **Volatility:** non-volatile
- **Access time:** _very slow_ (milliseconds)
- **Bandwidth:** moderate
- **Capacity:** very large
- **Density:** very high
- **Technology:** magnetic coating + spinning platters + moving heads
- **Cost per bit:** lowest of all major storage types
- **Usage:** long-term storage
    

#### Disk Structure
- **Track:** concentric circle on the platter
- **Sector:** smallest read/write unit of a track
    
#### Data Access Components
- **Seek time:** moving head to correct track
- **Rotational latency:** waiting for the correct sector
- **Transfer time:** reading/writing bits once aligned
    

Mechanical nature → the primary bottleneck.
### 4.5 Flash Memory
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
- **Cost per bit:** more expensive than disk, cheaper than DRAM

#### Usage 
SSDs, firmware storage, embedded systems




---


## 5. Performance


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

Block (or line)
> Fixed-size units of data

Fault
> used to mean failure of a component

Hit Rate (5.1)
> The fraction of memory accesses found in a level of the memory hierarchy

Miss rate (5.1)
> The fraction of memory accesses not found in a level of the memory hierarchy

Hit time (5.1)
>The time required to access a level of the memory hierarchy, including the time needed to determine whether the access is a hit or a miss

Miss penalty (5.1)
> The time required to fetch a block into a level of the memory hierarchy from the lower level, including the time to access the block, transmit it from one level to the other, insert it in the level that experienced the miss, and then pass the block to the requestor

Register file
> A state element that consists of a set of registers that can be read and written by supplying a register number to be accessed.

State element (7.7)
> A memory element.

Synchronous system (7.7)
> A memory system that employs clocks and where data signals are read only when the clock indicates that the signal values are stable.

Tag (5.3)
> A field in a table used for a memory hierarchy that contains the address information required to identify whether the associated block in the hierarchy corresponds to a requested word.

Valid bit (5.3)
> A field in the tables of a memory hierarchy that indicates that the associated block in the hierarchy contains valid data.

Temporal Locality
> The locality principle stating that if a data location is referenced then it will tend to be referenced again soon.

Spatial Locality
> The locality principle stating that if a data location is referenced, data locations with nearby addresses will tend to be referenced soon.

# References
Lab 12