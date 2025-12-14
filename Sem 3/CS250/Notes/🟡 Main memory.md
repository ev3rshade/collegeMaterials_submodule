Opened 22:38

Status:

Tags: cs250

Topic: 4

Prev Note: [[➡️ Cache]]  Next note: [[🟡 Address Spaces]] or [[Disk]]


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


## 2 Virtual Memory
> a technique that uses main memory as a "cache" for secondary storage
> 
> See [[🟡 Address Spaces]] for info on:
- Physical <--> virtual address translation
- Paging (accessing virtual memory)


## 3 Direct Memory Access (DMA)
> transferring data directly to/from main memory
- CPU only sets up the transfer
- Improves performance for high-speed devices

# References
## Textbook
- Chapter 5
	- 5.2