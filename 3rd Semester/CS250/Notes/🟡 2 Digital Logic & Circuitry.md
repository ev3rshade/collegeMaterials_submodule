Opened 15:48

Status: cs250

Tags: [[Computer Architecture]] #abstraction

# Digital Logic

---
## 1 Signals and Electrical Behavior
### 1.1 Signal States
#### Asserted
> A signal is logically high or true
#### Deasserted
> A signal is logically low or false


#### Active High logic
> represents truth table logic 1 values with the higher voltage level of the two voltages
#### Active Low logic
>represents a logic 1 value with the lower voltage level of the two voltages


### 1.2 Transitions
#### Rising Edge
0 --> 1
#### Falling Edge
1 --> 0


### 1.3 Control vs. Data Signals
#### Control signal
> Used for selection (e.g., multiplexors) or to direct the operation of a functional unit. (blue lines in textbook images)

#### Data signal
> Carries information that is transformed or stored. (black lines in in textbook images)




---
## 2 Types of Logic Systems
#### Combinational logic
> Logic with **no memory**; output depends only on current inputs
#### Sequential logic
> Logic **with memory**; output depends on current inputs **and** stored state.

#### Systems with State Elements
> a system with elements that have internal storage
- Registers
- Memories
- Any component with a clock input
- Latches and flip-flops




---
## 3 Fundamental Logic Components
### 3.1 Transistor
> An on/off switch controlled by an electric signal.
> Forms the basis of gates.

### 3.2 Basic Gates
- **AND**
- **OR**
- **NOT** (inverter)
- **NAND** - inverted AND
- **NOR** - inverted OR

### 3.3 Latches and Simple Storage
#### S'R' Latch
> is a basic digital memory circuit that stores one bit of information and is constructed using two NOR or NAND gates
- Input - S (Set) and R (Reset)
- Output - Q
#### D Latch
>a basic digital circuit that stores a single bit of informatio
- input - 'D' data (when its control signal (Enable/Clock) is active (transparent))
- function - locks that data (when the control signal goes inactive (opaque))




---
## 4 Boolean Algebra & Logic Representation

#### 4.1 Boolean Expressions
#### Sum of products
> logical representation that employs a logical sum (OR) of products (terms joined using the AND operator).
> e.g. u AND v OR x AND y = u * v + x * y (boolean algebar)
### 4.2 DeMorgan's Laws
> $$\neg(P \land Q) \equiv \neg P \lor \neg Q \quad  \neg(P \lor Q) \equiv \neg P \land \neg Q$$
#### 4.3 Truth Tables
> a function with $k$ variables requires $2^{k}$ rows

**Don't cares** - an informal expression of indifference or a technical term in digital logic for inputs that don't matter



---
## 5 Structured Logic Components
components of a logic system (circuit) built from the fundamental components


### 5.1 Data Stream
#### Bus
>a group of N wires used to carry N bits 
>of data simultaneously from place to place
#### Multiplexer (MUX)
> (selector) uses control signals to select one of the inputs and direct it to the output, acting as a data selector or a "many-to-one" switch
- **Selector value:** (control value) The control signal that is used to select one of the input values of a multiplexor as the output of the multiplexor.
#### Demultiplexer (DEMUX)
> a digital circuit that takes a single data input and routes it to one of several possible output lines, controlled by selection lines

### 5.2 Encoder / Decoder
> **Encoders*** convert $2^N$ lines of input into a code of $N$ bits and **Decoders*** decode the $N$ bits into $2^N$ lines

- **Decoder**:
    - Input: $n$ bits
    - Output: $2^n$ lines
    - Exactly **one output is asserted** for each input.
    - Example: **3-to-8 decoder**
        
- **Encoder**:
    - Input: $2^n$ lines
    - Output: $n$ bits
    - Converts a single asserted input into a binary code.

### 5.3 Programmable Logic Structures
#### Programmable logic array (PLA)\
> “A logic element with complemented inputs and two stages:
> 	1. **AND stage** forms product terms
> 	2. **OR stage** forms sum terms”

##### Read-only memory (ROM)
> Implements logic by treating input values as **addresses** and outputs as **stored words**.
- **Programmable ROM (PROM)**: A form of read-only memory that can be programmed when a designer knows its contents.



## 6 Timing
Gate Delays and stuff

---
## 7 Example Circuits & How They Work

### 7.1 Half Adder
#### Purpose
Adds two 1-bit binary inputs (A and B).

#### Outputs
- **Sum** = $A \oplus B$   
- **Carry** = $A \cdot B$ 

#### How It Works
- The **sum** is high when exactly one input is high → implemented with an XOR gate.  
- The **carry** is high only when both inputs are high → implemented with an AND gate.

**Circuit Components:** 1 XOR gate, 1 AND gate.



---
### 7.2 Full Adder

#### Purpose
Adds three 1-bit binary inputs (A, B, and Carry-in).
#### Outputs
- **Sum** = \( $A \oplus B \oplus C_{\text{in}}$\)  
- **Carry-out** = $(A \cdot B) + (C_{\text{in}} \cdot (A \oplus B$)) 

#### How It Works
- Built from **two half adders** and an OR gate.  
- First half adder adds **A** and **B**.  
- Second half adder adds the intermediate **sum** and **$C_{\text{in}}$**.  
- Carry-out is produced by OR’ing the carry outputs of the two stages.

**Circuit Components:** 2 XOR, 2 AND, 1 OR



---
### 7.3 2-to-1 Multiplexer

#### Inputs
- **D0**, **D1** (data inputs)  
- **S** (select)
#### Output
-  Y = ($\neg S \cdot D0) + (S \cdot D1)$ 


### How It Works
- If **S = 0**, output is **D0**.  
- If **S = 1**, output is **D1**.  
- Select line **S** ANDs with **D1**, while **¬S** ANDs with **D0**.  
- Outputs of both AND gates feed into an OR gate.

**Circuit Components:** 2 AND, 1 NOT, 1 OR.



---

### 7.4 3-to-8 Decoder

#### Inputs
- **A2, A1, A0** (3-bit binary input)
#### Outputs
- Eight output lines: **D0, D1, …, D7**


#### How It Works
Each output is the AND of input bits in either true or complemented form.

Examples:
- $D0 = \neg A2 \cdot \neg A1 \cdot \neg A0$ 
- $D5 = A2 \cdot \neg A1 \cdot A0$ 

Only one AND gate matches the binary input pattern → only one output is asserted.

**Circuit Components:**  
- 3 NOT gates  
- 8 AND gates

---

### 7.5 Set–Reset Latch (SR Latch using NOR Gates) (Lab 03)

#### Inputs
- **S** (set)  
- **R** (reset)
#### Outputs
- $Q, \neg Q$

### How It Works
- Formed from **cross-coupled NOR gates**.  
- If **S = 1**, latch sets → **Q = 1**.  
- If **R = 1**, latch resets → **Q = 0**.  
- If both inputs are **0**, the latch holds its previous state.  
- **S = R = 1** is an invalid/unstable condition.

**Circuit Components:** 2 NOR gates with feedback.

---

### 7.6 D Latch (Basic Memory Element)

#### Inputs
- **D** (data)  
- **EN** (enable)
#### Output
- **Q**
### How It Works
- When **EN = 1**, **Q follows D**.  
- When **EN = 0**, **Q retains its previous value**.  
- Internally constructed from an SR latch with gating logic that maps **D → (S, R)**.


**Circuit Components:**  
- 1 SR latch  
- 2 AND gates  
- 1 NOT gate


---
# Active Recall Questions
1. How many outputs does a 3 input decoder have?


---


# Information that needs to be included
Setup time
> The minimum time that the input to a memory device must be valid before the clock edge.

Hold time
> The minimum time during which the input must be valid after the clock edge.

Finite-state machine
> A sequential logic function consisting of a set of inputs and outputs, a next-state function that maps the current state and the inputs to a new state, and an output function that maps the current state and possibly the inputs to a set of asserted outputs.

Next-state function
> A combinational function that, given the inputs and the current state, determines the next state of a finite-state machine.

Field programmable devices (FPD)
> An integrated circuit containing combinational logic, and possibly memory devices, that are configurable by the end user.

Programmable logic device (PLD)
> An integrated circuit containing combinational logic whose function is configured by the end user.

Field programmable gate array (FPGA)
> A configurable integrated circuit containing both combinational logic blocks and flip-flops.

Simple programmable logic device (SPLD)
> Programmable logic device, usually containing either a single PAL or PLA.

Programmable array logic (PAL)
> Contains a programmable and-plane followed by a fixed or-plane.

Antifuse
> A structure in an integrated circuit that when programmed makes a permanent connection between two wires.

Lookup table (LUTs)
> In a field programmable device, the name given to the cells because they consist of a small amount of logic and RAM.
# References
## Lectures
[[CS250 LEC Boolean Alg, Comb Ckts, TT to Ckt - GB Adams.pdf]]
[[CS250 LEC Pointing and data bus selection - GB Adams.pdf]]
[[CS250 LEC Adding & Remembering - GB Adams.pdf]]
## Textbook Chapters
- Chapter 7
	- 7.1 - 7.3
	- 
	- 7.8
	- 7.12
	- 

## Labs
[[CS250 Lab01 Course Introduction.pdf]] - circuit diagram is incorrect
[[CS250 Lab03 S'R' Latch.pdf]]