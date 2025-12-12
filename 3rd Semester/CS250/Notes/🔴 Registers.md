Opened 15:34

Status:

Tags: [[🟡 Memory]]

# Registers
> A **register file** is a small, fast set of state elements inside the CPU.  
> accessed using register numbers (IDs) and supply operands for instructions.

## 1 Characteristics
- **Volatility:** volatile
- **Access time:** fastest in entire system (single cycle or sub-cycle)
- **Bandwidth:** extremely high (multiple read/write ports)
- **Capacity:** very small (tens to low hundreds of bytes)
- **Technology:** implemented using **SRAM-like flip-flops**
- **Access granularity:** word-level (defined by ISA)
- **Cost per bit:** highest of all memory types

## Usage
##### Memory access
Base registers
> register used for address computation (base + offset)
    
Destination register
> register that receives results of an instruction

#### Related registers
##### Program Counter (PC)
> register that holds the address of the next instruction


## Register Banks




# References
## Textbook
- Chapter 7
	- 7.7-7.8