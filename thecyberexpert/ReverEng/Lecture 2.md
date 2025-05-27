### Different modes in Operating system:
An error in one program can adversely affect many processes, it might modify data of another program or also can affect the operating system. For example, if a process stuck in the infinite loop then this infinite loop could affect the correct operation of other processes. So to ensure the proper execution of the operating system, there are two modes of operation: User Mode and Kernel Mode.
![[Pasted image 20250424194517.png]]
User Mode doesn't have many privileges. It has to be dependent on Kernel mode for even the basic of tasks. Processes are a part of the user mode/user space. Whenever User has to execute something, the process provides a system call to the kernel mode to perform the specific task.
The systems calls work in the following way: 
![[Pasted image 20250424194426.png]]
We can see all the system calls that can be performed by the system in the /usr/include/x86_x64-linux-gnu/asm/unistd_64.h file.
We can work with system calls using C.
For more information about system calls in C : https://www.geeksforgeeks.org/input-output-system-calls-c-create-open-close-read-write/