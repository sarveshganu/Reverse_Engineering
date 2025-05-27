## Reverse engineering using common tools
`file {filename}`: tells us about file type and stripped or not stripped
`ldd {filename}`: tells what files are linked during linking
`nm {filename}`: used to show symbols(labels) in the file
`strings {filename}`: prints every printable(ASCII) words in file, not code
`cat {filename}`: to show file
`ltrace {filename}`: shows us all the library functions called <b>during execution</b>
`strace {filename}` : shows us all system calls <b>during execution</b>
`readelf -a {filename}`: gives us a lot of info about file

Static vs Dynamic analysis: Static analysis refers to analysis done without running the executable. Before this we did static analysis
Dynamic Analysis is running the file and reverse engineering it.