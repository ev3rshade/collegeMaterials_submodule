10-30-2025 01:00

Status: #cs250

Tags: [[Circuitry]]

Chapters: 1.2 7.7
# Timing
> clocking and timing used to execute instructions and wait for data to load

## Delay
#### Propagation Delay
> how 
#### Latency
>the time delay between when a user sends a data request and when they receive a response
- Use latency: Number of clock cycles between a load instruction and an instruction that can use the result of the load without stalling the pipeline.

# Clocks (7.7)
## Clocking methodology
> The approach used to determine when data is valid and stable relative to the clock

##### Edge-triggered clocking
- a clocking scheme in which all state changes occur on a clock edge
- Allows for state elements to be read and written in same clock cycle without creating a race
###### Clock edge
- a quick transition from low to high

##### Single-cycle Implementation
- an implementation in which an instruction is executed in one clock cycle
- cons - too slow to be practical


# References