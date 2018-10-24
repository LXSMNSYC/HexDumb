# HexDumb
An esoteric language written in Lua

# What is HexDumb
It is an esoteric language I wrote in Lua. As the pun in the name suggests, you code with 2-digit hexadecimals. HexDumb works like some variants of assembly languages.
```
# A Hello World program in HexDumb #
40 48 40 45 40 4C 40 4C 40 4F 40 20 40 47 40 4F 40 52 40 4C 40 44
```

## Features
### Call Stack
The program that is run and interpreted by HexDumb is called the Call Stack. Call Stack contains the instruction calls and values needed by the program. The Call Stack also serves as the memory stack of the program, which makes HexDumb a reflective esoteric language: a language that allows you to modify itself on runtime.
### Registers
Just like Assembly variants, HexDumb uses registers. There 4(or 5, depends on how you interpret it) registers: A, B, C, D and Accumulator. These registers handle bytes separate from the call stack.
### Memoization
All instructions that transforms the value memoizes the output i.e. Bitwise instructions.
### Instructions
Here are the following Instructions:
#### Exit Program
| Instruction | Description |
| ----------- | ----------- |
| 00 | Exits the program |
#### Load to Register
| Instruction | Description |
| --- | --- |
| 01 [byte] | Load to Register A |
| 02 [byte] | Load to Register B |
| 03 [byte] | Load to Register C |
| 04 [byte] | Load to Register D |
| 05 [byte] | Load to Accumulator |
#### Push to Stack
| Instruction | Description |
| --- | --- |
| 10 [byte] | Push the next value to the end of the Call Stack |
| 11 | Push Register A to the end of the Call Stack |
| 12 | Push Register B to the end of the Call Stack |
| 13 | Push Register C to the end of the Call Stack |
| 14 | Push Register D to the end of the Call Stack |
| 15 | Push the Accumulator to the end of the Call Stack |
#### Pass Values
| Instruction | Description |
| --- | --- |
| 31 | Pass Register A to Accumulator |
| 32 | Pass Register B to Accumulator |
| 33 | Pass Register C to Accumulator |
| 34 | Pass Register D to Accumulator |
| 35 | Pass Accumulator to Register A |
| 36 | Pass Accumulator to Register B |
| 37 | Pass Accumulator to Register C |
| 38 | Pass Accumulator to Register D | 
| 51 | Pass Register A to the next Stack Position |
| 52 | Pass Register B to the next Stack Position |
| 53 | Pass Register C to the next Stack Position |
| 54 | Pass Register D to the next Stack Position |
| 55 | Pass Register Acc to the next Stack Position |
| 61 [byte] | Pass Register A to an Specific Stack Position |
| 62 [byte] | Pass Register B to an Specific Stack Position |
| 63 [byte] | Pass Register C to an Specific Stack Position |
| 64 [byte] | Pass Register D to an Specific Stack Position |
| 65 [byte] | Pass Register Acc to an Specific Stack Position |
#### Jumps
| Instruction | Description |
| --- | --- |
| F0 [byte] | Jumps to the position given by the next byte |
| FA | Jumps to the position given by Register A |
| FB | Jumps to the position given by Register B |
| FC | Jumps to the position given by Register C |
| FD | Jumps to the position given by Register D |
| FF [byte] [byte] | Jumps to the position given by the next two bytes as a 16-bit value |
#### Bitwise
##### AND
| Instruction | Description |
| --- | --- |
| 0A | Perform AND between Register A and Accumulator |
| 0B | Perform AND between Register B and Accumulator |
| 0C | Perform AND between Register C and Accumulator |
| 0D | Perform AND between Register D and Accumulator |
| 4A [byte] | Perform AND between Register A and the next byte |
| 4B [byte] | Perform AND between Register B and the next byte |
| 4C [byte] | Perform AND between Register C and the next byte |
| 4D [byte] | Perform AND between Register D and the next byte |
| 4E [byte] | Perform AND between Register Accumulator and the next byte |
##### OR
| Instruction | Description |
| --- | --- |
| 1A | Perform OR between Register A and Accumulator |
| 1B | Perform OR between Register B and Accumulator |
| 1C | Perform OR between Register C and Accumulator |
| 1D | Perform OR between Register D and Accumulator |
| 5A [byte] | Perform OR between Register A and the next byte |
| 5B [byte] | Perform OR between Register B and the next byte |
| 5C [byte] | Perform OR between Register C and the next byte |
| 5D [byte] | Perform OR between Register D and the next byte |
| 5E [byte] | Perform OR between Register Accumulator and the next byte |
##### XOR
| Instruction | Description |
| --- | --- |
| 2A | Perform XOR between Register A and Accumulator |
| 2B | Perform XOR between Register B and Accumulator |
| 2C | Perform XOR between Register C and Accumulator |
| 2D | Perform XOR between Register D and Accumulator |
| 6A [byte] | Perform XOR between Register A and the next byte |
| 6B [byte] | Perform XOR between Register B and the next byte |
| 6C [byte] | Perform XOR between Register C and the next byte |
| 6D [byte] | Perform XOR between Register D and the next byte |
| 6E [byte] | Perform XOR between Register Accumulator and the next byte |
##### NOT
| Instruction | Description |
| --- | --- |
| 3A | Perform NOT to Register A |
| 3B | Perform NOT to Register B |
| 3C | Perform NOT to Register C |
| 3D | Perform NOT to Register D |
| 3E | Perform NOT to Accumulator |
##### LSHIFT
| Instruction | Description |
| 7A | Perform LSHIFT to Register A by Accumulator |
| 7B | Perform LSHIFT to Register B by Accumulator |
| 7C | Perform LSHIFT to Register C by Accumulator |
| 7D | Perform LSHIFT to Register D by Accumulator |
| 9A [byte] | Perform LSHIFT to Register A by the next byte |
| 9B [byte] | Perform LSHIFT to Register B by the next byte |
| 9C [byte] | Perform LSHIFT to Register C by the next byte |
| 9D [byte] | Perform LSHIFT to Register D by the next byte |
| 9E [byte] | Perform LSHIFT to Accumulator by the next byte |
##### RSHIFT
| Instruction | Description |
| 8A | Perform RSHIFT to Register A by Accumulator |
| 8B | Perform RSHIFT to Register B by Accumulator |
| 8C | Perform RSHIFT to Register C by Accumulator |
| 8D | Perform RSHIFT to Register D by Accumulator |
| AA [byte] | Perform RSHIFT to Register A by the next byte |
| AB [byte] | Perform RSHIFT to Register B by the next byte |
| AC [byte] | Perform RSHIFT to Register C by the next byte |
| AD [byte] | Perform RSHIFT to Register D by the next byte |
| AE [byte] | Perform RSHIFT to Accumulator by the next byte |

