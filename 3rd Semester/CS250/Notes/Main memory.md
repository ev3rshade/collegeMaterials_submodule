Opened 22:38

Status:

Tags:

# Main memory

## 1 Technology

### DRAM (5.2)
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




# References