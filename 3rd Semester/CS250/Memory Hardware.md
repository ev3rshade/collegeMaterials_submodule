Opened 13:17

Status:

Tags: [[Memory]]

# Memory Hardware
###### Unit - byte
kilo | mega | giga | tera | peta | exa  | zetta | yotta
kibi | mebi | gibi | tebi | pebi | exbi | zebi | yobi

# ==Registers== #revise

Register file
> A state element that consists of a set of registers that can be read and written by supplying a register number to be accessed.

### Program Counter
> a special CPU register that holds the memory of the next instruction to be executed

##### Memory Access
- **Base register** + Offset
- Destination register - the register that receives the result of an operation

## Volatile /nonvolatile
### Volatile
#### SRAM (5.2)
- integrated circuits that are memory arrays with (usually) a single access port that can provide either a read or a write
- typically use six to eight transistors per bit of memory
- faster and less dense than DRAM
#### DRAM (5.2)
> Memory built as an ic. random access
- use only one transistor per bit of storage --> it cannot be kept indefinitely and must periodically be refreshed
- they are much denser and cheaper per bit than SRAM

DRAM organization
- Banks - series of rows
- successful bits transferred on each clock edge in bursts
![[Screenshot 2025-12-10 025555.png]]

#### Non volatile
##### Disk Memory
> a magnetic hard disk
- **Track** - One of thousands of concentric circles that make up the surface of a magnetic disk
	- **Sector** - One of the segments that make up a track on a magnetic disk; a sector is the smallest amount of information that is read or written on a disk

- Process of accessing data from a disk
	- **Seek** - The process of positioning a read/write head over the proper track on a disk
	- **Rotational latency** - Also called rotational delay. The time required for the desired sector of a disk to rotate under the read/write head; usually assumed to be half the rotation time
	- **Transfer time** - The time required to transfer a block of bits
- A magnetic disk is a MECHANICAL DEVICE!!!
##### Flash Memory
> a type of _electrically erasable programmable read-only memory_ (EEPROM) (semiconductor) (more expensive per bit)




# References