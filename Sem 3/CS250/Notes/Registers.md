Opened 15:34

Status:

Tags: cs250

Topic: 4

Prev note: [[➡️ Memory]] [[3 Programs]] Next note: 
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

## 2 Usage
##### Memory access
Base registers
> register used for address computation (base + offset)
    
Destination register
> register that receives results of an instruction

### Register Purpose in Programs
[[3 Programs]]

| Registers | Name                | Used For                  | Preserved |
| --------- | ------------------- | ------------------------- | --------- |
| X0–X7     | Arguments / Results | Parameters, return values | ❌         |
| X8        | Indirect result     | Large returns             | ❌         |
| X9–X15    | Temporaries         | Scratch values            | ❌         |
| X16–X17   | IP0/IP1             | Linker / temp             | ❌         |
| X18       | Platform            | OS-specific               | ❌         |
| X19–X27   | Saved               | Long-lived values         | ✅         |
| X28       | SP                  | Stack pointer             | ✅         |
| X29       | FP                  | Frame pointer             | ✅         |
| X30       | LR                  | Return address            | ✅         |
| X31       | XZR                 | Constant zero             | N/A       |


## 3 Register File
> The entire collection of general-purpose registers and the logic to access them, acting as fast, on-chip memory for the CPU.

**Register Bank (Specific Implementation):** A segment or group of registers within the larger file, often used for




# References
## Textbook
- Chapter 7
	- 7.7-7.8