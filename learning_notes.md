# NEW NOTES

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

- **INT 3** - or CCh; is the actual breakpoint instruction => gdb will overwrite the actual instruction to int 3 when you set a breakpoint
- **NOP** - nop = 90h; nop is a instruction that does nothing, useful for nopslides
  - **nopslide** - when you dont know the exact address of your shellcode you can do many nops before that so that you have a higher chance of hitting the nopslide that will lead to your shellcode
- **int 80** - used to invoke a syscall
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

#### Function calls

- **32-Bit** - parameters are saved on the stack
- **64-Bit** - parameters are saved in registers
  - **if too many parameters** - first parameters are saved in registers, rest on the stack

### Memory

#### ASLR

- **Address space layout randomization**
- without ASLR 32Bit Code is at 0x80...
- without ASLR 64Bit Code is at 0x40...

#### Stack

- **0xbffff...** - memory addr frame

#### Heap

- ?

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

#### Format string exploit

- With **printf()** you can use **'%x / %s / %d'** to leak values from the stack
- first spam many **%x** until you find the place of the stack, where your input will be stored
- then you know the **%x** padding until your input shows up
- you can then find the address of a variable for example and write it as input
- then you can use **%n** to write to that address and therefore change the value of the variable
- **%4$x** - will give the 4th. value of the stack
- **%4$30x** - 4.th value with a padding of 30 spaces (useful because **%n** will write the amount of printed characters to the stack)
- to overwrite the value with **%n**, you can 'devide' the address so you dont have to have millions of spaces printed on the screen
  - just do it in small steps and smaller numbers => 0x0806804d=0x08069cb0 => 0x0806804d=9cb0 / 0x0806804d+2=0806


### Global Offset Table

- has the addresses of different functions
- can be used with format string exploit to redirect code execution

### Global Linkage Table

- pushes the index on the stack, then starts the linking process which will find the address of the function and update the Global Offset Table, then it will also execute the function
