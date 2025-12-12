10-30-2025 12:40

Status: #cs250

Tags: [[Data Dependency]] [[Parallelism]]

Chapters: 1.2
# Pipelining
> overlapping parts of a processes, executing them simultaneously to increase efficiency

### Stages of an Instruction
1. Instruction Fetch (IF) 
	1. Source: Instruction memory (IM)
2. Instruction Decode/register file read (ID)
3. Execution (EX)
	1. ALU
4. Memory access (MEM)
	1. Source: Data Memory (DM)
5. Write back (WB)

## Timing
Equation for time it takes to execute $n$ instructions in a $k$ stage pipeline assuming no stalls
$$
\text{Number of Clock Cycles } = n + k - 1
$$

## Hazards (4.7)
Caused by Data Dependency (see Tags)

### 1. Types of Hazards
##### Structural Hazard
>when a planned instruction cannot execute in the proper clock cycle because the hardware does not support the combination of instructions that are set to execute
#### Data Hazard
> when a planned instruction cannot execute in the proper clock cycle because data that is needed to execute the instruction are not yet available
##### Load-use data hazard
> a specific form of data hazard in which the data being loaded by a load instruction has not yet become available when it is needed by another instruction
##### Control Hazard (branch hazard)
> When the proper instruction cannot execute in the proper pipeline clock cycle because the instruction that was fetched is not the one that is needed; that is, the flow of instruction addresses is not what the pipeline expected.
### 2. Methods to resolve Hazards
##### Instruction reordering
- changing the order of instruction to resolve data dependency issues
##### Forwarding (bypassing)
- a method of resolving a data hazard by retrieving the missing data element from internal buffers rather than waiting for it to arrive form programmer-visible registers of memory
Forwarding scenarios
![[Screenshot 2025-12-10 013459.png]]
##### Pipeline stall (bubble)
- a stall initiated to resolve a hazard
NOP
> an instruction that does no operation to change state
##### Branch [[Prediction]]
> A method of resolving a branch hazard that assumes a given outcome for the conditional branch and proceeds from that assumption rather than waiting to ascertain the actual outcome
- See [[problem lab10 8]]

###### Dynamic branch prediction
- Prediction of branches at runtime using runtime information.
- **Branch prediction buffer:** (branch history table). A small memory that is indexed by the lower portion of the address of the branch instruction and that contains one or more bits indicating whether the branch was recently taken or not.
![[2 Source Material/College Materials/3rd Semester/CS250/attachments/Screenshot 2025-12-10 014144.png]]






### 3. Hazard notations
1a. EX/MEM.RegisterRd = ID/EX.RegisterRn1
1b. EX/MEM.RegisterRd = ID/EX.RegisterRm2
2a. MEM/WB.RegisterRd = ID/EX.RegisterRn1
2b. MEM/WB.RegisterRd = ID/EX.RegisterRm2

Rn1 = first source operand
Rm2 = second source operand

### 4. Exceptions
Pipelined implementations treat exceptions as another form of control hazard


## Fallacies and Pitfalls (4.14)
Fallacy: Pipelining is easy
Fallacy: Pipelining ideas can be implemented independent of technology
- technology advancements change the pipelining methods and hazard mitigation

Pitfall: Failure to consider instruction set design can adversely impact pipelining.

## Terminology
###### Latency (Pipeline)
> The number of stages in a pipeline or the number of stages between two instructions during execution

Branch target buffer
> A structure that caches the destination PC or destination instruction for a branch. It is usually organized as a cache with tags, making it more costly than a simple prediction buffer.

Correlating predictor
> A branch predictor that combines local behavior of a particular branch and global information about the behavior of some recent number of executed branches.

Tournament branch predictor
> A branch predictor with multiple predictions for each branch and a selection mechanism that chooses which predictor to enable for a given branch.
# References
Lab 08
Lab 10