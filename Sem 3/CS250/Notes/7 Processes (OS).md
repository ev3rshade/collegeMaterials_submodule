Opened 12-12-2025 18:07

Status:

Tags: [[CS250 Computer Architecture - Class Outline]]

Prev Topic: [[4 Memory + Address Spaces]] Next Topic: [[🔴 Control and Task Management]]

Prev Note: [[🟡 Address Spaces]] Next Note: 
# Process
> (Program execution)
> A **process** is a program in execution together with its execution state and **private virtual address space**.





---
## 1 Process Address Space
- Each process has a **private virtual address space**
- Virtual addresses may be identical across processes but map to different physical memory
- Enables isolation and protection

Protection
> Hardware/OS mechanisms preventing processes from interfering with each other or the OS

#### Swap space
> The space on the disk reserved for the full virtual memory space of a process.


### 1.1 Page Replacement and Scheduling
(Process-Level)
- Replacement policies (e.g., LRU) are enforced by the OS
- Decisions are made per process or globally




---
## 2 Process Creation and Execution
### 3.1 Steps
- OS creates a process 
- Virtual address space is created
- Page tables initialized per process
- Memory may be loaded lazily (on demand paging)


### 3.2 Execution Modes
**User mode**
> Restricted mode used by application processes

**Supervisor mode (kernel mode)**
> a privileged mode used by the operating system to manage hardware, memory, and processes. (think `root` in linux

**System Calls**
> A special instruction that transfers control from user mode to supervisor mode using the exception mechanism (think `sudo` in linux)



### 3.3 Task-level prarallelism
> (Process-level parallelism) Utilizing multiple processors by running independent programs simultaneously.
- Requires multiple processors or cores
- Managed by the operating system scheduler




---
## 3 Process State
### Key Components
- **Program Counter (PC)** – next instruction address
- **Registers** – execution context
- **Stack Pointer**
- **Page table pointer**
    

### Context Switching
> Saving and restoring processor state to allow CPU sharing among processes

Includes:
- PC
- Registers
- Memory management info

Context switches introduce overhead.



---
# Active Recall
- Problems chp 5.7.6

# References
## Textbook
- Chapter 5
	- Section 5.7