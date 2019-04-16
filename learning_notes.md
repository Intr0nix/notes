# LEARNING NOTES

## LINUX

### SOME COMMANDS

- **cd** - change directory
- **cp** - copy file
- **mv** - move file
- **pwd** - prints current working directory
- **man** - manual page
- **ls** - show content of the current location
- **cat** - show content of file
- **touch** - create new file
- **rm** - remove file
- **mkdir** - make new directory
- **echo** - print sth
- **uname** - system info
- **free** - memory usage
- **df** - disk space usage
- **ps aux** - process information
- **id** - current user id
- **hexdump** - data in hex
- **grep** - filter output
- **find** - shows location of a file
- **wget** - get webpage as text
- **chmod** - change permissions of a file
- **env** - shows environment variables
- **file** - outputs type of file
- **sudo &lt;command&gt;** - execute &lt;command&gt; as superuser/root
- **whereis** - shows path to that file

### PIPES

**cat file | grep xyz** - only shows lines of file, containing 'xyz'

### INTERESTING FILES

- **~/.bashrc** - will be executed everytime the terminal is opened
- **~/.vimrc** - same as bashrc but with vim instead of the terminal
- **/etc/passwd** - local linux users
- **/etc/shadow** - local password hashes
- **/etc/group** - local account groups
- **/etc/hostname** - system hostname
- **/etc/profile** - system environment variables
- **~/.ssh/** - ssh files/keys
- **~/.bash_history** - users bash history

### VIM

- **$ vim -o file1 file2** - opens both files split vertically
  - **ctrl + w + -> / ctrl + w + <-** - change cursor between the files
- **:set number** - adds line numbers
- **:syntax on** - enables syntax highlighting
- **:w** - write / save
- **:q** - quit
- **:!command** - executes command as if in terminal
  - **:!python %** - executes the current file (python)
- **i** - enter insert mode
- **o** - enter insert mode with a new line below your cursor
- **shift + o** - enter insert mode with a new line above your cursor
- **yy** - copy line
- **p** - paste line
- **dd** - delete line
- **shift + v** - highlight multiple lines

## PROGRAMMING

### C

#### example Program

```C
1 \#include <stdio.h>
2  int main(int argc, char *argv[]) {
3     printf("$USER");
4     return 0;
5 }
```

#### explanation

line 1: adds standard i/o library<br/>
line 3: **$USER** - env variable with username<br/>
line 4: return 0 if no error / return 1 if there was an error

#### compile

$ gcc program.c -o program -Wall

#### example usage

$ ./program argument1 argument2

- **argc** - is 3
- **argv** - is \[program, argument1, argument2\]

### PYTHON

#### useful things

- **#!/usr/bin/python2.7** - can start the program like every other one (./program)
- **import sys** - so you can use sys.argv or write to stderr
- **python -c 'print "A"\*(4+16\*3+14)'** - prints A 4+16\*3+14 times

#### convert numbers

- **chr(0x41)** - hex to ASCII
- **hex(123)** - decimal to hex
- **bin(123)** - decimal to binary
- **int('1111',2)** - binary to decimal
- **hex(int('1111',2)** - binary to hex
- **struct.unpack("I", "ABCD")\[0\]** - ASCII to decimal
- **hex(struct.unpack(">I", "ABCD")\[0\])** - ASCII to hex (> is for changing the order of the hex numbers)
- **struct.pack("I", 0x41500000)** - hex to ASCII

## STUFF (just collecting atm)

### Registers

- **RIP / EIP / IP** - points to the address of the next instruction
- **RAX** - 64-Bit Register
  - **EAX** - lower 32-Bit
    - **AX** - lower 16-Bit   
      - **AH** - higher 8-Bit
      - **AL** - lower 8-Bit
- **RSP / ESP / SP** - stores the address of the top of the stack
- **FLAGS** - register that stores the flag bits (like Carry flag, Zero flag or Parity flag)
- **RBP / EBP / BP** - base / starting address of the stack

### Assembly

- **mov eax,0x05** - stores value '0x05' in eax
- **mov eax,\[0x400125\]** - stores value?, thats written in address 0x400125 (in memory), in eax
- **jumps, branches or calls** - used to change the instruction pointer -> control flow
  - **jumps** - unconditional jump
  - **branches** - conditioned with the FLAGS register status bits (e.g. je (jump equal))
  - **calls** - push the current IP on the stack, so the RET can later pop it off and keep going where the CALL left off, and jump
- **push** - push sth on the stack
- **pop** - pop the last value of the stack
- **test eax,eax** - returns 0 if strcmp before had 2x the same string
- **jne** - jumps if zeroflag is 0

### Memory

#### Stack

- area at the (bottom / top) ? of memory

### some helpful tools

- **strings** - displays strings of printable characters in files
- **ltrace** - traces library calls of a program
- **strace** - traces system calls and signals of a program
- **objdump -d** - disassembles the whole file
- **objdump -h** - displays header information
  - **.text** - where the code is written in memory
  - **.rodata** - read-only data where the strings are written in memory
- **binwalk** - for analyzing a binary file

### gdb

- **set disassembly-flavor intel** - intel syntax
- **disassemble main** - shows assembler code for main function
- **break \*main** - sets breakpoint at the start of main function
- **break \*addr** - sets breakpoint at the address
- **run (arguments)** - starts the program
- **info registers** - displays content of registers
- **si** - step one instruction
- **ni** - same as si, but doesnt follow function calls
- **x/s addr** - prints value at that address
- **set $rip=0x1234** - change register values
- **info proc mappings** - show mapped address spaces
- **define hook-stop** - executes every command, given after this one, every step
- **x/wx $esp+0x5c** - displays byte, written in that address
- **x function** - shows the starting address of the function and the first byte
- **x/1i $eip** - examine 1 instruction at the instruction pointer
- **x/8wx $esp** - examine 8 words as hex at the stack pointer
- **x/s $esp** - examine stack as string
- **find start_addr, +9999999, "string"** - displays addresses in that memory field, that contain the given string

### radare 2

- **aaa** - analyze and autoname functions
- **afl** - prints all found functions
- **?** - for help
  - **x?** - what you can append to x (x could be 'a' or sth else) and what is does
- **s sym.main** change current location (here to main function)
- **pdf** - print disassembly of the current function
- **VV** - enter visual mode to see control graph
  - **arrow keys** - move "camera" around
  - **tab** - select other blocks
  - **shift + h/j/k/l** - move block around
  - **p** - cycle through different representations
  - **?** - displays help
  - **shift + r** - randomize colors

#### disassemble
**$ r2 -d file**

- **db addr** - set breakpoint at address
- **VV**
  - **:dc** - runs the program
  - **s** - step instruction
  - **shift + s** - step instruction without following function calls
- **dr** - displays content of registers
  - **dr rip=0x01** - set rip 0x01
- **afvn previous_name new_name** - change variable name (old one was set by radare2)
- **ood arguments** - reload the binary
- **V!** switch to 'debugging overview'?

### hide password from strings command

#### idea:
loop over the password and add the hex values of the ascii characters, if the sum is the same as the right password, its correct

#### problem:
others are correct as well and its easy to reverse the algorithm and then bruteforce correct passwords

### Kernel

#### Privileges

- **User mode** - privilege level 3
- **Kernel mode** - privilege level 0

#### Syscalls

- fundamental interface between an application and the linux kernel
- used to execute operations on privilege level 0
- to use you have to write your values into the right register then invoke the syscall

#### MMU

- translates between virtual and physical memory addresses

### exploitation

#### Shell

- **echo $SHELL** - displays what shell is being used
- **/bin/bash** - better shell
- **$ echo "import pty; pty.spawn('/bin/bash')" > /tmp/asdf.py<br/>**
  **$ python /tmp/asdf.py** - also spawn better shell
  
#### setuid

- **-rwsr-xr-x** - s is setuid bit, its set so this program will be run as the owner of the file

#### buffer overflow

- Buffer: 64Bit
- Input: 72Bit
- => The Byte thats too long will get written on the stack, even though the buffer is to small, so you can overwrite other variables

##### buffer overflow -> redirecting the program

- ebp and eip are stored on the stack, so when you overwrite the whole stack, you are able to change the values, that will be poped into ebp and eip and therefore control the instruction pointer.

##### buffer overflow -> code execution

- overwrite the instruction pointer value on the stack to a memory address that will hit your code.
- because memory addresses may differ a little, use a nop slide (many nops before your actual code) and set the instruction pointer
  value to a memory address that will likely hit your nop slide.
- place the shellcode right after the nop slide
- shell will instantly close, so you have to do:
  **$ (python exploit.py ; cat) | program**
  
- if you are not allowed to ret to the stack, you can ret to the ret itself and then when the ret is executed again, it will get the 
  stack pointer from the stack, and use it for the instruction pointer so you will be able to jump to the stack again
  
##### ret2libc

- find the string **/bin/sh** with the command: **string -a -t x /lib/libc-\*.\*\*.\*.so | grep "/bin/sh"** (\* -> version number)
- then add the offset to the starting addr to get the memory addr where the string is written
- then write this address to the stack, so it will used for the instruction pointer after the ret
- remember to use **$ (python exploit.py ; cat) | program** if needed
