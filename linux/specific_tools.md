# Help for specific tools

## VIM

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

## gdb

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

## radare 2

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

### disassemble
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
- **V!** switch to 'debugging overview'
