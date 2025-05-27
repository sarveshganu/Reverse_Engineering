### Registers 
When a CPU is processing some data, lets say addition, it will take a lot of time to fetch the operands from memory which will slow down the processing. So to combat this, CPU registers were introduced. These are tiny memory devices in CPU that are used to store intermediate data.  Below is a visualization of a few registers used in CPUS.
![[Pasted image 20250424191747.png]]
Each general purpose register has following structure with their naming conventions:
![[Pasted image 20250424192639.png]]
Along with these general purpose registers, there is a special register called Instruction pointer which points to the current instruction in the program. The 64 bit naming convention for it is RIP and 32 bit convention in EIP.
We can access these registers in our terminal by using their naming conventions, to store small values in them 
![[Pasted image 20250424193250.png]]
