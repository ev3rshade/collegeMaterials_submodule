Opened 20:47

Status: #cs250 

Tags: [[🟡 Memory]]

# Address Spaces

Byte addressing, bit addressing

### Types of addressing

#### Immediate addressing
> the operand is a constant with the instruction itself
#### Register addressing
> the operand is a register
#### PC-relative addressing
> an addressing regime in which the address is the sum of the *program counter* (PC) and a constant in the instruction
#### Base or displacement addressing
> the operand is at the memory location whose address is the sum of a register and a constant in the instruction


## Physical and Virtual Address

![[Screenshot 2025-12-10 040607.png]]

Physical address
> An address in main memory
#### Virtual Memory (5.7)
> A technique that uses main memory as a "cache" for secondary storage
##### Virtual Address
> An address that corresponds to a location in virtual space and is translated by address mapping to a physical address when memory is accessed.
###### Virtual memory for large virtual addresses
Single-level page tables for large addresses need huge memory (e.g., 0.5 TiB).
Techniques used to reduce storage amount needed
- Limit registers let tables grow only as needed in one direction.
- Two-segment tables handle heap/stack growth but not sparse memory.
- Inverted and paged tables reduce memory use via hashing or virtual storage.
- Multi-level tables enable sparse large address spaces with more complex translation.


### Address translation
> (address mapping). The process by which a virtual address is mapped to an address used to access memory.

Segmentation
> A variable-size address mapping scheme in which an address consists of two parts: a segment number, which is mapped to a physical address, and a segment offset.

Page table
> The table containing the virtual to physical address translations in a virtual memory system, typically indexed by the virtual page number; each entry in the table contains the physical page number for virtual page if currently in memory.

#### Translation-lookaside buffer (TLB)
> A cache that keeps track of recently used address mappings to try to avoid an access to the page table. Each entry includes:
- physical page address
- tag
- status bits

![[Screenshot 2025-12-10 040607 1.png]]

Flowchart for address translation using TLB
![[Screenshot 2025-12-10 041801.png]]


#### Handling TLB Misses
1. The page is present in memory, and we need only create the missing TLB entry.
2. The page is not present in memory, and we need to transfer control to the operating system to deal with a page fault.
3. MUST be asserted by the end of the same clock cycle as memory access
##### ESR and ELR
> ELR (the exception link register) and ESR (the exception syndrome register) are two of the special ARMv8 control registers to help with page faults, TLB misses, and exceptions.

Virtual memory miss combinations: possible and impossible
![[Screenshot 2025-12-10 041929.png]]

### Exceptions
See [[Exceptions]]


## Address ranges
Conditional branches - +-2^18 words or 2^18 x 4 bytes

## Devices related to addressing
#### Address BUS


## Terminology
Aliasing
> A situation in which two addresses access the same object; it can occur in virtual memory when there are two virtual addresses for the same physical page.

Dirty bit
> indicates if a page has been written since being read into memory

Page fault
> An event that occurs when an accessed page is not present in main memory.

Protection
> A set of mechanisms for ensuring that multiple processes sharing the processor, memory, or I/O devices cannot interfere, intentionally or unintentionally, with one another by reading or writing each other's data. These mechanisms also isolate the operating system from a user process.

Reference bit
> (use bit or access bit) A field that is set whenever a page is accessed and that is used to implement LRU or other replacement schemes.

Swap space
> The space on the disk reserved for the full virtual memory space of a process.


# References