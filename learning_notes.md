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
- **i** - enter insert mode
- **o** -enter insert mode with a new line

## PROGRAMMING

### C

#### example Program

1 \#include &lt;stdio.h&gt;<br/>
2  int main(int argc, char *argv[]) {<br/>
3  &nbsp;&nbsp;&nbsp;&nbsp;printf("$USER");<br/>
4  &nbsp;&nbsp;&nbsp;&nbsp;return 0;<br/>
5 }

#### explanation

line 1: adds standard i/o library<br/>
line 3: **$USER** - env variable with username<br/>
line 4: return 0 if no error / return 1 if there was an error

#### compile

$ gcc program.c -o program -Wall

#### example usage

$ ./program argument1 argument2

- **argc** - is 3
- **argv** - is \[./program, argument1, argument2\]

