# HexDumb
An esoteric language written in Lua
# Table of Contents
* [What is HexDumb](#what-is-hexdumb)
* [Features](#features)
  * [Call Stack](#call-stack)
  * [Memoization](#memoization)
  * [Registers](#registers)
  * [Keys](#keys)
  * [Comments](#comments)
  * [Instructions](#instructions)
    * [Utilities](#utilities)
    * [Bitwise](#bitwise)
      * [Byte-To-Address](#byte-to-address)
      * [Address-To-Address](#address-to-address)
    * [Arithmetic](#arithmetic)
      * [Byte-To-Address](#byte-to-address-1)
      * [Address-To-Address](#address-to-address-1)
    * [Conditional Statements](#conditional-statements)
      

# What is HexDumb
It is an esoteric language I wrote in Lua 5.1. As the pun in the name suggests, you code with 2-digit hexadecimals. HexDumb works like some variants of assembly languages. 
HexDumb is also a reflective language, it allows to modify itself during runtime.
```
# A Hello World program in HexDumb #
06 48 06 45 06 4C 06 4C 06 4F 06 20 06 57 06 4F 06 52 06 4C 06 44
```
[Back to Top](#hexdumb)
## Features
### Call Stack
The program that is run and interpreted by HexDumb is called the Call Stack. Call Stack contains the instruction calls and values needed by the program. The Call Stack also serves as the memory stack of the program, which makes HexDumb a reflective esoteric language: a language that allows you to modify itself on runtime.

[Back to Top](#hexdumb)
### Memoization
All instructions that transforms the value memoizes the output i.e. Bitwise instructions.

[Back to Top](#hexdumb)
### Registers
Just like Assembly variants, HexDumb uses registers. Registers allows you to store bytes separate from the stack. There are 8 Registers (A, B, C, D, E, F, G, H).

[Back to Top](#hexdumb)
### Keys
Calling some instructions in HexDumb requires the use of Keys. Keys are hexadecimal values which describes the how the next byte is treated for the instruction call.
Here is the key table:

| Key | Description |
| :---: | --- |
| F0 | Tells the instruction call to access Register A |
| F1 | Tells the instruction call to access Register B |
| F2 | Tells the instruction call to access Register C |
| F3 | Tells the instruction call to access Register D |
| F4 | Tells the instruction call to access Register E |
| F5 | Tells the instruction call to access Register F |
| F6 | Tells the instruction call to access Register G |
| F7 | Tells the instruction call to access Register H |
| F8 | Tells the instruction call to access the Top Stack |
| F9 | Tells the instruction call to push the Top Stack |
| FA | Tells the instruction call to access the next byte |
| FB | Tells the instruction call to access the previous byte |
| FC | Tells the instruction call to access the byte from the current position |
| FD | Tells the instruction call to access an specific Stack position given by the next byte |
| FE | Tells the instruction call to access an specific Stack position given by the next short (two bytes) |

[Back to Top](#hexdumb)
### Comments
Life is not complete without any comment blocks in your code:
```
# This is a comment block #
```

[Back to Top](#hexdumb)
### Instructions
Guide:
```
<instr> [key] (byte (byte)) [byte]

<instr> - instruction code
[key] - provide a key value (required)
(byte) - optional, only provide if the key provided is FD
(byte byte) - optional, only provide if the key provided is FE
[byte] - provide a byte (required)

The whole term for [key] (byte (byte)) is called an address.
```

[Back to Top](#hexdumb)
#### Utilities
Utilities are called utilities for some reason.

| Instruction | Syntax | Description |
| :---: | :---: | --- |
| 00 | 00 | Terminates the program. |
| 01 | `01 [key] (byte (byte)) [byte]` | Load a byte to an address. | 
| 02 | `02 [key] (byte (byte)) [key] (byte (byte))` | Pass/Move/Copy the value of the first address to the second address. |
| 03 | `03 [key] (byte (byte)) [key] (byte (byte))` | Swaps the value of the two addresses. |
| 04 | `04 [key] (byte (byte))` | Jumps to stack position provided by the address. |
| 05 | `05 [byte]` | Outputs byte as a number. |
| 06 | `06 [byte]` | Outputs byte as a character. |
| 07 | `07 [key] (byte (byte))` | Outputs the value at the address as a number. |
| 08 | `08 [key] (byte (byte))` | Outputs the value at the address as a character. |
| 0A | `0A [key] (byte (byte))` | Reads an input as a number and puts it on the address. |
| 0B | `0B [key] (byte (byte))` | Reads an input as a character and puts it on the address. |
| 0C | `0C [key] (byte (byte))` | Reads an input as a byte (hexadecimal) and puts it on the address. |

[Back to Top](#hexdumb)
#### Bitwise
Bitwise operations. There are two types: byte-to-address and address-to-address. Byte-To-Address modifies the value of the given address. Address-To-Address modifies the value of the first address.
##### Byte-To-Address
| Instruction | Syntax | Description |
| :---: | :---: | --- |
| 11 | `11 [key] (byte (byte)) [byte]` | AND |
| 12 | `12 [key] (byte (byte)) [byte]` | OR |
| 13 | `13 [key] (byte (byte)) [byte]` | XOR |
| 14 | `14 [key] (byte (byte))` | NOT |
| 15 | `15 [key] (byte (byte)) [byte]` | LSHIFT |
| 16 | `16 [key] (byte (byte)) [byte]` | RSHIFT |
| 17 | `17 [key] (byte (byte)) [byte]` | ROL |
| 18 | `18 [key] (byte (byte)) [byte]` | ROR |

[Back to Top](#hexdumb)
##### Address-To-Address
| Instruction | Syntax | Description |
| :---: | :---: | --- |
| 21 | `21 [key] (byte (byte)) [key] (byte (byte))` | AND |
| 22 | `22 [key] (byte (byte)) [key] (byte (byte))` | OR |
| 23 | `23 [key] (byte (byte)) [key] (byte (byte))` | XOR |
| 24 | `24 [key] (byte (byte))` | NOT (similar to the instruction #15 NOT) |
| 25 | `25 [key] (byte (byte)) [key] (byte (byte))` | LSHIFT |
| 26 | `26 [key] (byte (byte)) [key] (byte (byte))` | RSHIFT |
| 27 | `27 [key] (byte (byte)) [key] (byte (byte))` | ROL |
| 28 | `28 [key] (byte (byte)) [key] (byte (byte))` | ROR |

[Back to Top](#hexdumb)
#### Arithmetic
There are only two for now: Addition and Subtraction. Similar to Bitwise, there are Byte-To-Address and Address-To-Address variations.
##### Byte-To-Address
| Instruction | Syntax | Description |
| :---: | :---: | --- |
| 31 | `31 [key] (byte (byte)) [byte]` | Addition |
| 32 | `32 [key] (byte (byte)) [byte]` | Subtraction |

[Back to Top](#hexdumb)
##### Address-To-Address
| Instruction | Syntax | Description |
| :---: | :---: | --- |
| 41 | `41 [key] (byte (byte)) [key] (byte (byte))` | Addition |
| 42 | `42 [key] (byte (byte)) [key] (byte (byte))` | Subtraction |

[Back to Top](#hexdumb)
#### Conditional Statements
There are three conditional instructions, both are an interpretation of an IF block. The first addresses provided will be used for condition purposes. The condition will result to true if the value at the given address is greater than 0, otherwise it is false.

| Instruction | Syntax | Description |
| :---: | :---: | --- |
| 51 | `51 [key] (byte (byte)) [key] (byte (byte)) [key] (byte (byte))` | If true, jumps to the second address, otherwise, it jumps to the third address. Also called as "Conditional Jump". |
| 52 | `52 [key] (byte (byte)) [key] (byte (byte)) [byte] [byte]` | If true, sets the value of the second address to the first byte, otherwise, the second byte. Also called as "Conditional Load". |
| 53 | `53 [key] (byte (byte)) [key] (byte (byte)) [key] (byte (byte)) [key] (byte (byte))` | If true, sets the value of the second address to the value of the third address, otherwise, the fourth address. Also called as "Conditional Pass". |

[Back to Top](#hexdumb)



