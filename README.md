<h1>Universal Machine (UM) </h1>

<h2> Description </h2>
This project is a software implementation of a simple virtual machine. This UM has these components:

- Eight general-purpose registers holding one word each
- A very large address space that is divided into an ever-changing collection of memory segments. Each segment contains a sequence of words, and each is referred to by a distinct 32-bit identifier. The memory is segmented and word-oriented
- An I/O device capable of displaying ASCII characters and performing
input and output of unsigned 8-bit characters
- A 32-bit program counter

The UM is initialized by providing it with a program, which is a sequence of 32-bit words. At each time step, an instruction is retrieved from the word in the 0 segment
whose address is the program counter. The program counter is advanced to the next word, if any, and the instruction is then executed. Most of these instructions operate on three registers and the registers are identified by a number (A, B, and C). Each number coded as a three-bit unsigned integer embedded in the instruction word. The UM recognizes 14 unique instructions specified by an Opcode from 0-13:

0. Conditional Move
    - Data inside register B gets moved to register A
1. Segmented Load
    - Register A loads the data from memory segment at the index of (value in register B, value in register C)
2. Segmented Store
    - Memory segemnt at the index of (value in register A, value in register B) stores the data in register C
3. Addition
    - Adds the values in registers B and C and stores the result in register A
4. Multiplication
    - Multiplies that values in registers B and C and stores the result in register A
5. Division
    - Divides (integer division) the value in reigtser B by the value in register C and stores the result in register A
6. Bitwise NAND
    - Takes the inverse of register B and register C and stores it in register A
7. Halt
    - Ends computation
8. Map Segment
    - A new memory segment where the length is equal to the value in register C is created, and initialized to all zeroes at the value in reigster B
9. Unmap Segment
    - memory segment at the value in register C is emptied, but not removed
10. Output
    - The value in register C is displayed on the I/O device immediately (only values from 0 to 255)
11. Input
    - Takes input from the I/O device (must be value 0 - 255) and stores it in register C
12. Load Program
    - Replaces memory segment at index 0 with memory segment at the index of the value in register B and sets the program counter to memory segment at index (0, value in register C)
13. Load Value
    - Stores the value of the last 25 bits of the instruction word to the register that corresponds to the three bits directly after the opcode

<h2> Languages Used </h2>

- <b> Rust </b> 
