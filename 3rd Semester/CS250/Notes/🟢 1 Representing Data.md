Opened 17:45

Status: cs250

Tags: [[Computer Architecture]]

Chapters: 

# Representing Data
## 1. Units
### Bits
> most fundamental unit of data in computing, representing a single binary value of either **0 or 1**, analogous to an on/off switch or true/false state, forming the basic building block for all digital information, from text and images to complex software
#### Least significant bit
> rightmost bit in an LEGv8 doubleword
#### Most significant bit
> leftmost bit in a LEGv8 doubleword

#### Word
> a natural unit of access in a computer, usually a group of 32 bits
> **Double word** --> double that


---
## 2. Representations

### 2.1 Binary Representation

Example used: **13** and **–13**

#### One's Complement
> Ex: 13 → 01101  
>    –13 → 10010

#### Two's Complement
> Ex: 13 → 01101  
>    –13 → 10011

#### Sign-magnitude
> Ex: 13 → 01101  
>    –13 → 11101

### 2.2 Hexadecimal Representation

> A base-16 numbering system using digits **0–9** and **A–F**.

**Example:**  
Binary: `1111 0001 1010 0100`  
Group into 4-bit chunks: `1111 | 0001 | 1010 | 0100`  
Convert each group:

- 1111 → **F**
    
- 0001 → **1**
    
- 1010 → **A**
    
- 0100 → **4**
    

**Hexadecimal value:** **0xF1A4**


### 2.3 Endianness

#### Big Endian

> Stores the **most significant byte first** (at the lowest memory address).  
> Human-friendly; matches the order we write numbers.

**Example:**  
Value: `0x12345678`  
Memory (low → high):  
`12 34 56 78`

#### Little Endian

> Stores the **least significant byte first** (at the lowest memory address).  
> Used by many modern architectures.

**Example:**  
Value: `0x12345678`  
Memory (low → high):  
`78 56 34 12`

### 2.4 Text
#### ASCII
> Character encoding scheme using 7/8 bits to represent characters such as letters, digits, punctuation, and control codes.

#### Purpose
- Universal communication between computers
- Data interchange

#### Components
- Printable characters
- Control characters

##### ASCII Design Criterion
- Ease of machine use

| ASCII | Hex | Binary    |
| ----- | --- | --------- |
| 0     | 30  | 0011 0000 |
| 1     | 31  | 0011 0001 |
| 2     | 32  | 0011 0010 |
| 3     | 33  | 0011 0011 |
| 4     | 34  | 0011 0100 |
| 5     | 35  | 0011 0101 |
| 6     | 36  | 0011 0110 |
| 7     | 37  | 0011 0111 |
| 8     | 38  | 0011 1000 |
| 9     | 39  | 0011 1001 |
### 2.5 Floating Point
[[IEEE Floating Point System]]

# References
## Lectures
[[CS250 LEC Adding & Remembering - GB Adams.pdf]]
[[CS250 LEC Data Representation - GB Adams.pdf]]
[[CS250 LEC IEEE 754 Floating Point - GB Adams.pdf]]
## Textbook Chapters