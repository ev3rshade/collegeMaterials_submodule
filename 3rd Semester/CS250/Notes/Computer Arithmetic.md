Opened 17:54

Status: #cs250

Tags: [[Circuitry]]

# Computer Arithmetic
#### Binary digit representation
1. Sign and magnitude representation
2. Two's complement
3. One's compelment
4. Biased notation
##### Overflow
> not enough bits to represent -- set with value instead of the result instead of the result

#### Hexadecimal represntation


## Storage
### Sign Extension
> repeatedly copying the sign to fill the rest of a register or memory location in order to place a correct representation of a number in a register
- used so numbers are properly formatted for arithmetic instructions 
- `LDURB` and `LDURH` used to load and sign extend the most significant bits
- `STURB` and `STURH` preserve the byte and halfword values, simply storing the registers in memory

## Operations
##### Addition
```
carry over:    1100
----------------------
			   1011
			+  0110
			   ----
			  10001
```
##### Subtraction
```
carry over:    0100
----------------------
			   1011
			-  0110
			   ----
			   0101
```
##### Multiplication

```
carry over:    0100
----------------------
			   1011
			x  0110
			   ----
			   0000
			  1011
			 1011
		 +  0000
		   --------
		   01000010
```
![[Screenshot 2025-12-09 122855.png]]
circuit does what we did above with bit shifting. The first step checks Multiplier0 to determine whether the multiplicand is added to the Product register. The second step shifts the Multiplicand register left 1 bit. The third step shifts the Multiplier register right 1 bit.
[[Moore's Law]]

##### Division
```
result:        1011
----------------------
			   01000010
			/  0110
			   ----
			    0110
			     0000
			      0110
			       0110
			   --------
			   00000000
```
![[Screenshot 2025-12-09 124711.png]]

[[Moore's Law]]
[[Prediction]] - **predict** several quotient bits per step

## Circuitry used
(see [[Circuitry]] for more info)
Arithmetic Logic Unit (ALU)
Registers

# References