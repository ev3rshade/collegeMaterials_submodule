Opened 22:47

Status:

Tags:

# Disk

## 1 Technology
> A **mechanical**, magnetic storage device. Non-volatile and extremely high capacity.

#### Characteristics
- **Volatility:** non-volatile
- **Access time:** _very slow_ (milliseconds)
- **Bandwidth:** moderate
- **Capacity:** very large
- **Density:** very high
- **Technology:** magnetic coating + spinning platters + moving heads
- **Cost per bit:** lowest of all major storage types
- **Usage:** long-term storage
    

#### Disk Structure
- **Track:** concentric circle on the platter
- **Sector:** smallest read/write unit of a track
    
#### Data Access Components
- **Seek time:** moving head to correct track
- **Rotational latency:** waiting for the correct sector
- **Transfer time:** reading/writing bits once aligned
    

Mechanical nature → the primary bottleneck.


# Active Recall
1. (true/false) In a magnetic disk, sequential block numbers are placed next to one another on a track Ex: Block 207 is placed after block 206.
	1. || False - Sequential blocks may be on different tracks. To speed up sequential transfers, blocks are ordered in serpentine fashion across a single surface, trying to capture all the sectors that are recorded at the same bit density. ||

# References
## Textbook
- Chapter 5
	- 5.2