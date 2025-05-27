## Reverse Engineering python files using bytecode
We can use `readelf -a {filename}|grep py` to check if a binary file is python file or not. If a binary file is a python file , we can  take a look at the pydata section. This is a setion like .text and .data but it is used by python to store bytecode and some other data.
We can use the following command to dump the bytecode section. 
`objcopy --dump-section pydata={file where bytecode will be stored} {b'filename}`
Now this file contains the bytecode and some other headers, and essential data, but it is in zlib compressed data format. To uncompress it, we can use pyinstxtractor.py tool (available on github) . This will give us an extracted folder.
![[Pasted image 20250501174924.png]]
From the above image we can see that there is a bytecode file .pyc which we can use the command `uncompyle6 crackme8.pyc > crackme8.py` to reverse the bytecode into the complete original python file. 
Note: uncompyle6 will have to be installed using `pip3 install uncompyle6`
Then we can reverse engineer it using the python file, as the python file is the complete original file and not pseudocode like C or C++. This is an advantage for us