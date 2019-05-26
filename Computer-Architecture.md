# Computer Architecture Lectures

- [x] [Lecture 1](#lecture-1):construction:
- [ ] [Lecture 2](#lecture-2)
- [ ] [Lecture 3](#lecture-3)
- [ ] [Lecture 4](#lecture-4)
- [ ] [Lecture 5](#lecture-5)
- [ ] [Lecture 6](#lecture-6)

## Lecture 1

**What is inside a computer?**
- There are five classic components of a computer.
  1. Processor:
    * Divided into two groups:
      - Data section:
          * also called datapath.
          * contains the registers and the Arithmetic Logic unit.
          * is capable of performing certain operations on data items.
      - Control section:
          * the control unit that generates control signals that direct the operation of memory and datapath.
          * control signals do the following:
            - tell memory to send or receive data.
            - tell the ALU what operation to perform.
            - route data between different parts of the datapath.

  2. Registers:
    * the storage element for data inside the CPU.
    * hold temporary data during calculations.
    * faster in accessing than memory.

  3. Main Memory:
    * Large collection of circuits, each capable of storing a single bit and is arranged in small cells.
    * Each cell has a unique address
    * Longer strings stored by using consecutive cells.
    <!-- place image of main memory -->

  4. System Bus:
    * Group of signal lines have the same function.
    * Allow transferring the signals between different parts of the computer and from one device to another.
    * There are three types of system buses:
      - data bus:
        * transfer data from CPU to memory and vice-versa.
        * connects I/O ports and CPU.
      - address bus: determine where the address of memory locations should be sent.
      - control bus: determine the operation.

      <!-- place image of system bus -->


there are two pieces of information that should be known to solve this example:
1. If there are N address lines in address bus, that means we can directly address 2^N of memory locations.
in other words, if we have N address lines, then our memory has 2^N cell.

2. The number of data lines used in the data bus is equal to the
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

**Levels of transformation**
<!-- place image of levels -->
* They create abstraction.
* Abstraction: A higher level only needs to know about the interface to the lower level, not how the lower level is implemented.
* it improves the productivity.

**Convert C program to machine language:**
<!-- place image of phases -->

* Machine Language is fundamental instructions expressed as 0s and 1s.
* Assembly Language is human-readable equivalent of machine language.
* Assembler converts assembly language program to machine language.
* Linker links separately assembled modules together into a single module suitable for loading and execution.
* Loader is a part of operating system and is responsible for loading executable files into memory and execute them.

**What is computer architecture?**
Simply:
computer architecture = Machine organization + Instruction Set Architecture.

* Instruction Set Architecture (ISA): Interfaces the software to the hardware, and provides support for programming.

<!-- place image of ISA -->
