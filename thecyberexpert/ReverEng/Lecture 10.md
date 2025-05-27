## Reverse engineering our first crackme
We can use the gdb debugger by using gdb command.
- `gdb ./your_program` : to debug a program
- `run`: to run the program
- `disassemble {function_name}`: to disassemble a particular function
- `set disassembly-flavour`: append att/intel to set which assembly we want
- `info functions`: run it before run instruction to see only the functions in this program
- `break *{address}`: to place a breakpoint at a particular address
- `info registers`: to see the registers in the program. Shows only when program is running and is at a breapoint
- `ni`: next instruction. To jump to next instruction
- `print {hex]`: tells us what the value is 
- `x/s {memaddress}`:  tells us what value is stored there
- `x/{number}{what we want to see} {memory address}` : 
   1) {number} : amount of what we wanna see
   2) {what we wanna see}:  a) h: hex    b) i: instruction   c) s: string
   3) {memory address}: of what address we wanna see it (*we can even put $rip to see current address's thing and for any register we wanna se, we gotta add $ before*)
