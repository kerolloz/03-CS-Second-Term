# Computer Architecture Lectures

- [x] [Lecture 1](#lecture-1)
- [x] [Lecture 2](#lecture-2)
- [ ] [Lecture 3](#lecture-3) :construction:
- [ ] [Lecture 4](#lecture-4)
- [ ] [Lecture 5](#lecture-5)
- [ ] [Lecture 6](#lecture-6)

## Lecture 1

### What is inside a computer?

There are **five** classic components of a computer:
1. **Processor**:
  * Divided into two groups:
    - **Data section (_data path_)**:
        * contains the registers and the Arithmetic Logic unit.
        * is capable of performing certain operations on data items.
    - **Control section**:
        * the control unit that generates control signals that direct the operation of memory and data path.
        * control signals do the following:
          - tell memory to send or receive data.
          - tell the ALU what operation to perform.
          - route data between different parts of the data path.
1. **Registers**:
  * the storage element for data inside the CPU.
  * hold temporary data during calculations.
  * faster in accessing than memory.
1. **Main Memory**:
  * Large collection of circuits, each capable of storing a single bit and is arranged in small cells.
  * Each cell has a unique address
  * Longer strings stored by using consecutive cells.
  ![main memory](./pics/ca/1.png)
1. **System Bus**:
  * Group of signal lines have the same function.
  * Allow transferring the signals between different parts of the computer and from one device to another.
  * There are **three** types of system buses:
    - _data_ bus:
      * transfers data from CPU to memory and vice-versa.
      * connects I/O ports and CPU.
    - _address_ bus: determines where the address of memory locations should be sent.
    - _control_ bus: determines the operation.
    ![system bus](./pics/ca/2.png)


there are two pieces of information that should be known to solve this example:
1. If there are N address lines in address bus, that means we can directly address 2^N of memory locations.
in other words, if we have N address lines, then our memory has 2^N cell.

1. The number of data lines used in the data bus is equal to the
size of data word that can be written or read.

*Example:*

How many memory locations can be addressed by a microprocessor with 14 address lines?

N = 14
then number of memory locations (or memory cells) = 2^N = 2^14 locations.

*Example:*

Suppose that a computer’s Main Memory has 1013 cells. How many address lines are needed in order for all the cells to be usable?

2^N = 1013
then to get N we need to take log for base 2 for both sides
log(2^N) = ceil(log(1013))
N =  9.

---

### Levels of transformation

![levels of transformation](./pics/ca/3.png)
![levels of transformation](./pics/ca/my-diagram.png)  

Abstraction
: A higher level only needs to know about the **interface** to the lower level, _not how the lower level is implemented._


### Convert C program to machine language:

![levels of transformation](./pics/ca/4.png)

Machine Language
: fundamental instructions expressed as 0s and 1s.

Assembly Language
: human-readable equivalent of machine language.

Assembler
: converts assembly language program to machine language.

Linker
: links separately assembled modules together into a single module suitable for loading and execution.

Loader
: part of operating system responsible for loading executable files into memory and execute them.

### What is computer architecture?

Simply,
>Computer Architecture = Machine organization + Instruction Set Architecture


### Instruction Set Architecture (ISA)
> * Interfaces the software to the hardware
> * provides support for programming.
> * provides the mechanism by which the software tells the hardware what should be done.

![ISA](./pics/ca/5.png)

## Lecture 2

### ISA Components
 - Storage cells: registers, memory.
 - Machine Instruction Set: set of possible operations.
 - The instruction format: Size and meaning of fields within the instruction.

**Every instruction need to specify four _(1 which +  3 where)_ things:**
1. Which operation to perform.
1. Where to find the operand or operands, if there are operands.
1. Where to put the result, if there is a result.
1. Where to find the next instruction.

*Example:*  

`MOVE.W D4, D5`  

MOVE => operation  
D4 => location of the operand  
D5 => location to put the result  
Find next instruction => implicitly in the word following this instruction.  


### Instruction Cycle

![Instruction Cycle](./pics/ca/6.png)

For example, to do the add instruction:

Fetch
: get the instruction from memory into the processor.

Decode
: internally decode what it has to do.

Execute
: take the values from the registers, actually add them together.

Store
: store the result back into another register.(_retiring_ the instruction)

### Classes of instructions

1. _Data movement instructions_: `Load, Store`
1. _Arithmetic and logic_ (ALU) instructions: `Add, Sub, Shift`
1. _Branch_ instructions(control flow instructions): `Br, Brz`

### Program Counter (PC)

* _incremented_ during the _instruction fetch_ to _point_ to the _next instruction_ to be executed.
* controls program flow.

### Branch target address

* A target address is specified in a `branch` or `jump` instruction.
* The target address is loaded into the PC, replacing the address stored there.
* A branch may be:
  - **Unconditional**, as is the C `goto` statement.
  - **Conditional**, depends on whether some condition within the processor state is true or false.

### Condition Code (CC)
> The bit(s) that describe the condition stored in it.
>> also called:
* the processor status word (PSW).
* the status register.

- **No** machine instruction corresponds directly to the conditional statements.

> The approach most machines take is to set various ___status flags___ within the CPU as a result of ALU operations.

- The instruction set contains a number of conditional branch instructions that test various of these flags and then branch or not according to their settings.

### Hypothetical machine models

there are **5** types of them:

|  address instruction  |                                             use                                             |
|:---------------------:|:-------------------------------------------------------------------------------------------:|
| 3 address instruction |                     memory addresses for both operands and the result.                      |
| 2 address instruction |                      overwrites one operand in memory with the result                       |
| 1 address instruction |                 a register **(accumulator)** hold one operand & the result.                 |
| 0 address instruction |              a CPU register **(stack)** to hold both operands and the result.               |
| 4 address instruction | like 3 address but also allows the address of the next instruction to specified explicitly. |

*[ALU]: Arithmetic Logic Unit
*[PSW]: Processor Status Word
*[ISA]: Instruction Set Architecture
*[PC]: Program Counter
*[CC]: Condition Code*

## Lecture 3

- it is known that for a 2-operand arithmetic instruction we need to specify:
1. The operation to be performed.
2. Location of the 1st operand.
3. Location of the 2nd operand.
4. Place to store the result.
5. Location of next instruction to be performed

- the variation in specifying the five items makes various types of hypothetical machine models.
- in each machine we study the encoding of an ALU instruction.



* assume the following:
 - data lines in data bus = 24 => then size of data word = 3 bytes.
 - address lines = 24 => then the size of address of each operand = 3 bytes
 - we have 128 instructions then every instruction is encoded in 7 bit = 8 Byte <!--replace = with approximation sign-->
<!-- make this part as a table -->    

1. 4-address machine:
<!-- place image for 4AM  -->
  - Number of bytes required for each instruction:
     number of operand's addresses(4) * size of address for each operand(3) + size of opcode(1) = 13 bytes.  
  *NOTE:* the instruction is fetched in 5 memory accesses => ceil(size of instruction / size of data word) = ceil(13/3).
  - Number of memory access:
    5 (for fetching the instruction) +
    2 (for fetching the 1st and 2nd operands) +
    1 (for storing the result) = 8 memory accesses

  *NOTE:* Because of the large instruction word size and number of memory accesses, the 4-address machine and instruction format is not normally seen in machine design.

2. 3-address machine
<!-- place image for 3AM  -->
  - An instruction of this machine specifies only 3 addresses in the list (1st operand, 2nd operand, and the result).
  - The address of next instruction is handled by The Program Counter (PC) register.
  - Number of bytes required for each instruction:
     number of operand's addresses(3) * size of address for each operand(3) + size of opcode(1) = 10 bytes.  
   *NOTE:* the instruction is fetched in 4 memory accesses => ceil(size of instruction / size of data word) = ceil(10/3).
  - Number of memory access:
    4 (for fetching the instruction) +
    2 (for fetching the 1st and 2nd operands) +
    1 (for storing the result) = 7 memory accesses


3. 2-address machine
<!-- place image for 2AM  -->
  - An instruction of this machine specifies only 2 addresses in the list (1st operand, 2nd operand).
  - The result is stored in the address of one of the operands.
  - The address of next instruction is handled by The Program Counter (PC) register.

  - Number of bytes required for each instruction:
     number of operand's addresses(2) * size of address for each operand(3) + size of opcode(1) = 7 bytes.  
   *NOTE:* the instruction is fetched in 3 memory accesses => ceil(size of instruction / size of data word) = ceil(7/3).
  - Number of memory access:
    3 (for fetching the instruction) +
    2 (for fetching the 1st and 2nd operands) +
    1 (for storing the result) = 6 memory accesses

4. 1-address machine (accumulator machine)
<!-- place image for 1AM  -->
  - An instruction of this machine specifies only 1 address (1st operand).
  - The Accumulator register is the source of 2nd operand and also the storage for the result.
  - The address of next instruction is handled by The Program Counter (PC) register.
  - Requires two special instructions:
      * LDA Addr; Load the content of Addr to accumulator.
      * STA Addr; Stores the content of accumulator to address Addr.
  - Generally provide a minimum in the size of both program and CPU memory required.
  - Number of bytes required for each instruction:
     number of operand's addresses(1) * size of address for each operand(3) + size of opcode(1) = 4 bytes.  
   *NOTE:* the instruction is fetched in 2 memory accesses => ceil(size of instruction / size of data word) = ceil(4/3).
  - Number of memory access:
    2 (for fetching the instruction) +
    1 (for fetching one operand or storing the result) = 3 memory accesses
