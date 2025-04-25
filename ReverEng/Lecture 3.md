### Assembly For Reverse Engineering

Assembly type: Intel x64 bit Linux assembly. The default assembler for intel is called <b>nasm</b>
Note: Here, destination and source can be a register or an immediate data but atleast one of them should be a register as the result will be stored in the register
#### 1) MOV {Destination} ,{Source}
Used to move data between general purpose registers. 
#### 2) ADD {Destination}, {Source}
Used to add data between two registers. The result is stored in the Destination register 
#### 3) SUB {Destination}, {Source}
Used to subtract data between two registers. Work same way as add
#### 4) CMP {Destination}, {Source}
Used to compare two different values. Works by checking the zero flag and the carry flag.
#### 5) TEST {Destination}, {Source}
Used to check if a particular value is zero or not. CMP subtracts to check if it is zero or not, TEST uses AND operation to check a particular register. Both destination and source register in this instruction are the same.
#### 6) JMP {Destination}
The destination provided can be a register or an address. 
#### 7) JE/JZ {Destination}
Jump if equal or jump if zero , jumps to the particular address if the zero flag is set (1).
#### 8) JNE/JNZ {Destination}
Jump if not equal. Works in same way as JE/JZ ,except it jumps if zero flag is reset (0)
#### 9) CALL {Destination}
Similar to JMP, wherein it jumps to the provided address, and executes instructions from there. However, once the instruction execution ends, Instruction register returns to the same memory address where the CALL instruction was present.
#### 10) RET 
This instruction is used together with CALL. Whenever the CALL instruction jumps to a particular address and starts executing instructions there, this instruction can be used to indicate to instruction register to return to the CALL address
#### 11) SYSCALL 
Its used to "system call". It checks the value of RAX to see which System call opcode is provided. If for example some data has to be provided like exit(11), RAX is used to store the instruction opcode 0x3C and the data 11 is stored in RDI as 0xB
### 12) imul {destination}, {source}, {immediate}
destination and source are registers and immediate is the number that is multiplied with them
### 13) idiv {register}
The value stored in rdx:rax registers is divided by the value in the provided register(register used cannot be rax or rdx) and stored in rax itself
