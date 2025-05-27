## Automated reverse engineering using angr in python
```python
#!/usr/bin/python3

import angr #download angr using  pip3 install angr
import angr.factory #subfolder of angr 

crackme = angr.Project('../../Downloads/./crackme9') #defining the project file
entry = crackme.factory.entry_state() #we can specify the entry address here or angr will find it for us automatically
manager = crackme.factory.simgr(entry) # implement manager at entry point

manager.explore(find=0x004022c1,avoid=0x004022cf)# we tell manager to explore the file and try to find key which leads to success and avoid wrong password output
if manager.found:
print(manager.found[0].posix.dumps(0)) #if the key is found, dump it using file operator 1, which is stdoutput
else:
print("Not Found!")
```