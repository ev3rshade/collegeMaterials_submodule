Opened 12-13-2025 22:22

Status:

Tags: cs250

Topic: 9

Prev Note: [[Processor Architecture]] Next Note:
# Special Parallel Architectures
## Grid Computing
> Uses idle resources of many distributed computers to solve large problems.

Characteristics:
- Tasks split into small independent units
- Redundancy used for correctness
    

Examples:
- BOINC
- Einstein@Home
- Rosetta@home
- nanoHUB@home
    

---

## MISD Architecture
> Multiple instruction stages operating on a single data stream.
- Rare in general-purpose computing
- Often appears as **data pipelining**
    

### Data Pipeline Example
- Internet routers processing packets
- Pipeline increases throughput, not latency
    

---

## Redundant Parallel Architectures
> Used to improve reliability rather than performance
- Multiple hardware units compute the same result
- Watchdog circuitry checks consistency
    

Uses:
- Fault detection
- Fault tolerance




# References