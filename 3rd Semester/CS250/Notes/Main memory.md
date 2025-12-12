Opened 22:38

Status:

Tags:

# Main memory

## 1 Technology

### DRAM
> Main memory technology using **1 transistor + capacitor per bit** which **requires periodic refresh.**

#### Characteristics

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


## Virtual Memory
> a technique that uses main memory as a "cache" for secondary storage

#### Virtual address
> An address that corresponds to a location in virtual space and is translated by address mapping to a physical address when memory is accessed


### Paging
#### Page
> a fixed-size block of virtual memory that the operating system uses for memory management

#### Page Table
> A data structure that tracks which virtual page number maps to which physical page number, acting as the OS's directory for memory

#### Page fault
> An event that occurs when an accessed page is not present in main memory.

### Types
##### Physically addressed cache
> A cache that is addressed by a physical address (an address in main memory)
##### Virtually addressed cache
> A cache that is accessed with a virtual address rather than a physical address



# Information to include
Protection
> A set of mechanisms for ensuring that multiple processes sharing the processor, memory, or I/O devices cannot interfere, intentionally or unintentionally, with one another by reading or writing each other's data. These mechanisms also isolate the operating system from a user process.

# References
## Textbook
- Chapter 5
	- 5.2