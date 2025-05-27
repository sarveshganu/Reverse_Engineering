## Debugging using radare2
`r2 -d ./yourprogram` : to launch radare2
`aaa`: to analyse all functions and all references
`afl`: to list all functions
`db {function}`: to put a breakpoint at a particualr function
`dc`: continue execution 
`V`: to see the assembly code 
`VV`: to see the assembly code in visual manner
`VV --> R`: to change colours
`VV --> S`: to move instruction pointer down
`VV --> P`: to change the format of view in VV as well as V
'VV --> ; ' : to access terminal inside VV
`ood {argument for program`: to run the program from start again, argument is optional
`dr`: to view status of registers
`drr`: to view detailed information about registers 


