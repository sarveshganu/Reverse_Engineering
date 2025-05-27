## Dealing with anti reversing technique: stripping 

Stripping is technique used to discourage reverse engineers. It basically removes symbols from a binary like main, and other function names. So it only uses their addresses to call the functions, stripping them from their names
``` bash
sg@sg-Aspire-A715-76G:~$ file Downloads/crackme8
Downloads/crackme8: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=f6af5bc244c001328c174a6abf855d682aa7401b, for GNU/Linux 2.6.32, stripped
```
We can use the `file` command to check if binary is stripped or not
Article on how to disassemble a stripped binary:
https://tr0id.medium.com/working-with-stripped-binaries-in-gdb-cacacd7d5a33
Basically, we want to find the  _lib_start_main_ function that calls the main function. The address in rdi register is the address of the main function.