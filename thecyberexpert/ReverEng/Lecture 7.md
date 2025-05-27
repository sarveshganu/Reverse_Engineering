### Comparing user input 
```nasm

GLOBAL  _start

section .text

_start:
   jmp main
main:
  mov rax,0
  mov rdi,0
  mov rsi,user_key
  mov rdx,64
  syscall

cmp_key:
 cmp rax,ogkey_l
 jne access_d
 mov rsi, original_key
 mov rdi,user_key
 mov rcx,ogkey_l
 repe cmpsb
 jne access_d


access_g:
  mov rax,1
  mov rdi,1
  mov rsi,access_granted
  mov rdx, access_g_l
  syscall
  jmp exit
access_d:
  mov rax,1
  mov rdi,1
  mov rsi,access_denied
  mov rdx, access_d_l
  syscall
exit:
 mov rax,60
 mov rdi,0
 syscall

section .data
 access_granted: db "Access Granted!",10
 access_g_l: equ $-access_granted
 access_denied: db "Access Denied", 10
 access_d_l: equ $-access_denied
 original_key: db "12345678"
 ogkey_l: equ $-original_key
section .bss
  user_key: resb 64

```