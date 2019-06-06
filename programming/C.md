# C

## variablies

### declare new variable

int variable = 0;

### change already declared variable

variable = variable + 1;

**IS THE SAME AS**

variable += 1;

**IS THE SAME AS**

variable++;

## conditions

if (var1 == var2) {
	printf("var1 equals var2");
} else if (var1 < var2) {
	printf("var1 is less than var2");
} else {
	printf("var1 is greater than var2");
}

## loops

while (true) {
	printf("this is an endless loop");
}


for (int i = 0 ; i < 12 ; i++) {
	printf("this will be printed 12 times");
}

## print variables

printf("variable1: %s/nvariable2: %s", variable1, variable2);

## example program

```C
#include <stdio.h>

int main(int argc, char *argv[]) {
	printf("text");
}
```

### information

- #include <stdio.h> - adds standard i/o library <br/>
- **argc** - is the count of arguments given, when the program is run in the cli
- **argv** - is an array with the arguments given, when the program is run in the cli

## compile your program (in the terminal)

$  gcc program.c -o program -Wall 
