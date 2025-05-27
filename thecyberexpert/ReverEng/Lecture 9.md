## Calculator in Assembly
```nasm
 %include "util.asm"

global _start

section .text

_start:
       jmp user_ip
user_ip:
    mov rdi,prompt
    call printstr
    call readint
    mov [uservalue1],rax
     mov rdi,prompt2
    call printstr
    call readint
    mov [uservalue2],rax
    mov rdi, prompt3
    call printstr
    mov rdi,uservalue3
    mov rsi,2
    call readstr
    mov rdi,[uservalue3]
    cmp rdi,43
    je addition
    cmp rdi,45
    je subtraction
    cmp rdi, 47
    je division
    cmp rdi,42
    je multiplication
    mov rdi, error
    call printstr
    jmp exitp

addition:
        mov rax, [uservalue1]
        add rax, [uservalue2]
        mov rdi,rax
        call printint
        jmp exitp
division:
        mov rax,[uservalue1]
        mov rbx, [uservalue2]
        idiv rbx
        mov rdi,rax
        call printint
        jmp exitp
multiplication:
        mov rdi,[uservalue1]
        imul rdi, [uservalue2]
        call printint
        jmp exitp
subtraction:
        mov rax, [uservalue1]
        sub rax, [uservalue2]
        mov rdi,rax
        call printint
        jmp exitp
exitp:
 call endl
 call exit0
section .data
 prompt: db "Enter operand 1: ",0
 prompt2: db "Enter operand 2: ",0
 prompt3: db "Enter your operation: ",0
 error: db "Please enter correct operation",10,0

section .bss
  uservalue1: resb 8
  uservalue2: resb 8
  uservalue3: resb 2
                           
```