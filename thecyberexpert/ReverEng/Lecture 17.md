## Dealing with Anti-Debug and Anti-VM techniques
To avoid analysis by reverse engineers, malware authors use anti debug and anti vm techniques.
**Anti Debug techniques:** Using the function _ptrace(PTRACE_TRACEME,0)_, we can check if any thing is tracking this process(the malware). If it is, we can ask the malware to take the necessary steps to evade it. 
**Anti VM techniques**: 
``` Pseudocode 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdint.h>

int main(int argc, char** argv) {
    printf("***********************\n");
    printf("**      rules:       **\n");
    printf("***********************\n\n");
    printf("* do not bruteforce\n");
    printf("* do not patch, find instead the…\n\n");

    char secret[] = "This is a top secret text message!";
    char idtr[10];

    // Store IDT register into idtr
    __asm__ volatile ("sidt %0" : "=m"(idtr));

    // Check byte 5 of the IDTR base
    if ((unsigned char)idtr[5] == 0xFF) {
        printf("VMware detected\n");
        exit(1);
    }

    printf("No VM detected\n");

    return 0;
}
```
In the above example the line, - uses the **`SIDT` (Store Interrupt Descriptor Table Register)** instruction to get the contents of the IDTR register, which is a CPU structure that stores the base address of the **Interrupt Descriptor Table (IDT)**.
`004013fc int80_t var_9e = __sidt_mems64(idtr);`
Normally, the value returned is in kernel space for real hardware — but in many virtualized environments (like VMware), the **IDT base address** can fall into **unusual ranges** or contain recognizable patterns.

So to evade this, we use binaryninjas or other analysis tools to patch them up and allow use to do analysis.