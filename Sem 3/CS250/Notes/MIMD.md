Opened 12-13-2025 22:18

Status:

Tags: cs250

Topic: 9

Prev Note: [[Processor Architecture]] Next Note: 

# MIMD
> Multiple processors executing independent instruction streams.

- Most common parallel architecture
    
- Parallelism is explicit to the programmer
    

---
## 1 MIMD Characteristics
- Program copy per processor
- Independent fetch-execute cycles
- Coordination via software
    

---

## 2 Synchronization Mechanisms
### Barriers
> All processes must reach the barrier before any proceed.
- Used for phase synchronization


#### Naïve Barrier Problem
- Can cause deadlock if reused improperly
    
#### Sense-Reversing Barrier
- Alternates barrier state encoding
- Prevents deadlock
    




---
## 3 Locks and Mutual Exclusion

### Why Locks Are Needed
- Prevent race conditions
- Ensure atomic updates
    

### Hardware Locks
- Only one processor may hold a lock
- Protect critical sections
    




---
## 4 Cache Coherence
- Multiple caches may hold inconsistent data
- Requires coherence protocols
    

---

## 5 Multiprocessor Overheads

Sources:
- Communication
- Synchronization
- Resource contention
    

Effects:
- Limits speedup
- Can reduce performance at scale



# Active Recall
# References