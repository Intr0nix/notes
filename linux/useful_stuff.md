# SOME USEFUL STUFF
## Some commands

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

## Pipes

**cat file | grep xyz** - only shows lines of file, containing 'xyz'

## Interesting files

- **~/.bashrc** - will be executed everytime the terminal is opened
- **~/.vimrc** - same as bashrc but with vim instead of the terminal
- **/etc/passwd** - local linux users
- **/etc/shadow** - local password hashes
- **/etc/group** - local account groups
- **/etc/hostname** - system hostname
- **/etc/profile** - system environment variables
- **~/.ssh/** - ssh files/keys
- **~/.bash_history** - users bash history

## Useful tools

- **strings** - displays strings of printable characters in files
- **ltrace** - traces library calls of a program
- **strace** - traces system calls and signals of a program
- **objdump -d** - disassembles the whole file
- **objdump -h** - displays header information
  - **.text** - where the code is written in memory
  - **.rodata** - read-only data where the strings are written in memory
- **binwalk** - for analyzing a binary file
