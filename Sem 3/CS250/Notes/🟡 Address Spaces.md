Opened 20:47

Status: 

Tags: cs250

Topic: 4

Prev Note: [[🟡 Main memory]] Next Note: [[7 Processes (OS)]]

# Address Space
> range of memory that a system, process, or device can use to identify data or instructions

Address spaces define **how memory is named and accessed**, independent of _who_ is running.




---
## 1 Addressing Basics

### 1.1 Data sizes
Addressing gives each unit of data size a unique address. There is:
- Bit addressing
- Byte addressing
- Word addressing

### 1.2 Addressing Modes in Instructions
#### 1.2.1 Immediate addressing
> the operand is a constant with the instruction itself
#### 1.2.2 Register addressing
> the operand is a register
#### 1.2.3 PC-relative addressing
> an addressing regime in which the address is the sum of the *program counter* (PC) and a constant in the instruction
#### 1.2.4 Base or displacement addressing
> the operand is at the memory location whose address is the sum of a register and a constant in the instruction





---
## 2 Physical and Virtual Addresses
### 2.1 Physical address
> An address that refers to an actual location in main memory (RAM).

### 2.2 Virtual memory
> A technique that uses main memory as a cache for secondary storage.
#### 2.2.1 Virtual address
> An address in virtual space that is translated into a physical address during memory access.
##### Components of a virtual address
- Virtual page number (specifies the page in the virtual memory)
- Page offset (specifies the precise byte location)


![[Screenshot 2025-12-10 040607.png]]





---
## 3 Paging
Exploits:
	- Spatial locality
	- reduce miss rate
### 3.1 Terminology
#### 3.1.1 Page
> a fixed-size block of virtual memory that the operating system uses for memory management

#### 3.1.2 Page Table
> A data structure that tracks which virtual page number maps to which physical page number, acting as the OS's directory for memory

##### Size of a Page Table
> $$ 
  \dfrac{\text{Virtual Addresss Space}}{\text{Page Size}} \times \text{Table Entry Size} 
  $$
#### 3.1.3 Page fault
> A virtual memory miss 
> (accessed page is not in main memory)



### 3.2 Large Virtual Address Spaces
Single-level page tables for large virtual addresses require excessive memory (e.g., ~0.5 TiB).

Techniques to reduce storage:
- **Limit registers** — tables grow only as needed in one direction
- **Two-segment tables** — handle heap/stack growth but not sparse memory
- **Inverted and hashed page tables** — reduce memory use via hashing
- **Multi-level page tables** — support sparse address spaces with hierarchical translation




---
## 4 Address Translation
> (address mapping). The process by which a virtual address is mapped to an address used to access memory.

##### Segmentation
> A variable-size mapping scheme where an address consists of a **segment number** and a **segment offset**.

### 4.1 Translation Lookaside Buffer (TLB)
> A cache that keeps track of recently used address mappings to try to avoid an access to the page table. Each entry includes:
- physical page address
- tag
- status bits

#### 4.1.1 TLB Translation Visualization
![[Screenshot 2025-12-10 040607 1.png]]

#### 4.1.2 TLB-based Address Translation Flow
![[Screenshot 2025-12-10 041801.png]]


#### 4.1.3 Handling TLB Misses
1. Page is in memory → create missing TLB entry
2. Page not in memory → raise page fault and transfer control to OS
3. Translation must complete within the same clock cycle as memory access

##### ESR and ELR (ARMv8)
> **ELR** (the exception link register) and **ESR** (the exception syndrome register) are two of the special ARMv8 control registers to help with page faults, TLB misses, and exceptions.


##### Virtual memory miss combinations: possible and impossible
![[Screenshot 2025-12-10 041929.png]]






---
## 5 Exceptions
### 5.1 Page Fault Exceptions
Handled by the operation system
1. Look up the page table entry using the virtual address
2. Select a physical page to replace (write back if dirty)
3. Load the referenced page from secondary storage

### 5.2 Exception enable
> (interrupt enable) Controls whether exceptions are allowed; ensures the processor state is safely saved before handling exceptions





---
## 6 Devices related to addressing
#### Address BUS




---
## 7 Terminology
Aliasing
> A situation in which two addresses access the same object; it can occur in virtual memory when there are two virtual addresses for the same physical page.



## Info that needs to be put somewhwere
###### Address ranges
Conditional branches - +-2^18 words or 2^18 x 4 bytes

# Active Recall
- Problems chapter 5.7.6

# References
## Textbook
- Chapter 5
	- 5.7