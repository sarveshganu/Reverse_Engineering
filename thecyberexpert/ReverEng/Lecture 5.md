## Taking user input in assembly
```nasm
global _start
section .text
_start: 
    mov rax,1
    mov rdi,1
    mov rsi, wlc
    mov rdx, wlc_length 
    syscall
user_input: 
    mov rax,0
    mov rdi,0
    mov rsi, input
    mov rdx , 100
    syscall
    mov rbx,rax
print_output:
    mov rax,1 
    mov rdi,1
    mov rsi,hello
    mov rdx,hello_length
    syscall
print_userip:
    mov rax,1
    mov rdi,1
    mov rsi,input
    mov rdx,rbx
    syscall
exit:
    mov rax,60
    mov rdi, 0
    syscall


section .data
    wlc: db "Enter you name: " ; db stands for define bytes
    wlc_length: equ $-wlc ; the $ sign signifies end of string, here $-wlc means                             ; End of string - beggining of string, so it counts bytes
                          ; of the string automatically
    hello: db "Hello, "
    hello_length: equ $-hello

section .bss
   input: resb 100        ; stands for reserve bytes, we are reserving 100 of them                           ; for user input



```