## Dealing with packed binaries
So, if we use the checksec command from the pwntools suite of tools, we can see if it has been packed using any packer.
```bash
sg@sg-Aspire-A715-76G:~/Downloads$ checksec crackme7
[*] '/home/sg/Downloads/crackme7'
    Arch:       amd64-64-little
    RELRO:      No RELRO
    Stack:      No canary found
    NX:         NX enabled
    PIE:        No PIE (0x400000)
    Packer:     Packed with UPX
```
In the above  example the code used the upx packer 
So we unpack it using `upx -d {filename}`. Then we can carry on with our reverse engineering . 
Amazing resource on packing and file storage:
https://dplastico.github.io/sin%20categor%C3%ADa/2022/04/21/packed-binaries.html