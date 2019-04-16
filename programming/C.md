# C

## Example program

```C
1 \#include <stdio.h>
2  int main(int argc, char *argv[]) {
3     printf("$USER");
4     return 0;
5 }
```

### explanation

line 1: adds standard i/o library<br/>
line 3: **$USER** - env variable with username<br/>
line 4: return 0 if no error / return 1 if there was an error

### compile

$ gcc program.c -o program -Wall

### example usage

$ ./program argument1 argument2

- **argc** - is 3
- **argv** - is \[program, argument1, argument2\]
