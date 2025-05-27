## Hello World in Assembly
Before we start: 
- `rax` - used to store temporary values. In the case of a system call], it should store the system call number.
- `rdi` - used to pass the first argument to a function.
- `rsi` - used to pass the second argument to a function.
- `rdx` - used to pass the third argument to a function.
``` nasm
;Global starting point
global _start
;;Definition of the text section
section .text
;; Entry point
_start:
    ;; Specify the number of the system call (1 is `sys_write`).
    mov     rax, 1
    ;; Set the first argument of `sys_write` to 1 (`stdout`).
    mov     rdi, 1
    ;;Set the second argument of `sys_write` to the reference of the `msg` variable.
    mov     rsi, hello
    ;; Set the third argument to the length of the variable's value (13 bytes).
    mov     rdx, 14
    ;; Call the `sys_write` system call.
    syscall
    ;; Specify the number of the system call (60 is `sys_exit`).
    mov    rax, 60
    ;; Set the first argument of `sys_exit` to 0. The 0 status code is success.
    mov    rdi, 0
    ;; Call the `sys_exit` system call.
    syscall

    
;;Definition of the static `data` section 
section .data
    ;;String `msg` variable with the value `Hello world!`
    hello: db 'Hello, World!'

	``` 