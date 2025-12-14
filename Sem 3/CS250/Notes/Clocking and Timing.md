10-30-2025 01:00

Status: 

Tags: cs250

Topic: [[🟡➡️ 2 Digital Logic & Circuitry]] [[🟡 5 Program Execution]]

Prev Note: [[🟡 5 Program Execution]] Next Note: [[Instruction Pipelining]]
# Clock
> a hardware timing signal that coordinates when state elements (registers, PC, memory) are updated.
- Clock period determines the maximum rate of instruction progress.


---
## 1 Clock Cycle Time
- Determined by the **slowest stage** in the datapath.
- Shorter clock cycles increase performance but require simpler stages.



---
## 2 Clocking Methodology
> Defines when data is considered valid and when state elements may change.

#### Edge-Triggered Clocking (synchronous execution)
- All state changes occur on a **clock edge** (usually rising edge)
- Prevents race conditions
- Allows reading and writing state in the same cycle


##### Clock Edge
> A rapid transition from low to high (or high to low) voltage level.



---
## 3 Timing and Clocking
> **Timing** concerns how long operations take and how hardware ensures data is valid when used.

### Delay
#### Propagation Delay
> The time it takes for a signal change at a component’s input to produce a stable change at its output.
- Determined by circuit complexity and physical properties
- Limits how fast a clock can run

#### Latency
> The delay between initiating an operation and observing its result.
- In processors: measured in **clock cycles**
- **Load-use latency**: number of cycles between a load instruction and the earliest instruction that can use its result without stalling

# References
## Textbook
- Chapter 1
	- 1.2
- Chapter 4
	- 
- Chapter 7
	- 7.7