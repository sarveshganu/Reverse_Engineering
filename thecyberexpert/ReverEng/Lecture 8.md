```nasm
%include "util.asm" ;include file which has common functions used
global _start

section .text
 _start:
    mov rdi,prompt
    call printstr ;call functions from the included file
    call readint
    mov [user_value],rax ;using [] makes it so that the value of rax goes into the memory location specified by user_value
    mov rbx,1

loop: mov rcx,[user_value]
    imul rcx,rbx
    mov rdi,rcx
    call printint
    call endl ;similar to c++ endl
    add rbx,1
    cmp rbx,11
    jne loop
    call exit0   ;exit0 exits the function and makes the value of rdi 0, so it esentially exits with return number as 0
section .data
 prompt: db "Enter a number: ",10,0 ;we have added null byte at end, cause printstr expectes string with null byte at end
section .bss
  user_value: resb 8        
```