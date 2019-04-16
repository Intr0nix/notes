# PYTHON

## Essentials

- **my_name = "name"** - Variable  
**%s acts as a placeholder for a string, while %d acts as a placeholder for a number** 

## interesting functions

- **range(16)** - returns 0-15
- **len(my_name)** - length of variable
- **my_name.lower()** - string in lower cases (dot notation => only strings)
- **my_name.upper()** - string in upper cases (dot notation => only strings)
- **max()** - returns largest number
- **min()** - returns smallest number
- **abs()** - returns distance from 0
- **type()** - returns data type
- **filter(lambda x: x != 1, var)** - filters string or list

## String formatting with %

- **print "Lets not go to %s. Tis a silly %s."%(string1,string2)**

## Userinput

- **variable = raw_input("What is your name?")**

## Date/Time

- **from datetime import datetime** - imports the library
- **now = datetime.now()** - save time right now to variable
- **now** => 2018-02-12 17:04:42.215200
- **now.year** => 2018
- **now.month** => 2
- **now.day** => 12

## Conditionals and Control Flow

- **'=='** - equal to
- **'!='** - not equal to
- **'&lt;'** - less than
- **'&lt;='** - less than or equal to
- **'&gt;'** - greater than
- **'&gt;='** - greater than or equal to

## Boolean Operators

True and True is True  
True and False is False  
False and False is False  
False and False is False  

True or True is True  
True or False is True  
False or True is True  
False or False is False  

Not True is False  
Not False is True  

not is evaluated first  
and is evaluated next  
or is evaluated last  

## Conditional Statement Syntax

```PYTHON
if 8 > 9:
  print "not true"
elif 8 < 9:
  print "true"
else:
  print "wont happen"
```

## Strings

- **"string"\[1\]** - => t
- **print "hey " + "its " + "me"** - string concatenation
- **var = "test123"**
  - **var.isalpha()** => false (true if only letters)
- **var\[4:len(var)\]** => 123
- **for char in string:** - does sth for every char in string

## Imports

- **import math** - usage: math.sqrt()
- **from math import \*** - usage: sqrt()

## Functions

```PYTHON
def name(n):
  print "n"
  return n + 1
  
```

## Lists

- **my_list = \["ele1","ele2"\]** - List
- **my_list\[3:5\]** - returns element 3 to 5-1=4
- **my_list.index('element1')** - returns index of the given element
- **my_list.insert(index,'string')** - inserts element with given string in given index
- **my_list.sort()** - sorts the list
- **my_list.remove('string')** - removes the given element from the list
- **my_list.pop(index)** - removes the element with the given index
- **for element in my_list:** - executes sth for every element in the list
- **print my_list\[::2\]** - prints every second element of my_list
- **print my_list\[::-1\]** - prints elements of my_list from last to first

## Dictionaries

- **dict = {'key1':value1,'key2':value2}** - you are able to use lists as values
- **dict\[newKey\] = newValue** - add new pair
- **dict.len()** - returns number of key/value pairs
- **del dict\[key\]** - deletes key/value pair with given key
- **for key in dict:** - does sth for every value in dict
- **dict.items()** - returns every key/value pair in dict
- **dict.keys()** - returns every key in dict
- **dict.values()** - returns every value in dict

## Bitwise operators

- **10 &lt;&lt; 3** - left shift by 3
- **10 &gt;&gt; 3** - right shift by 3
- **4 & 5** - AND
- **5 | 4** - OR
- **2 ^ 9** - XOR
- **~3** - NOT

## Classes

```PYTHON

class Car(object):
  def __init__(self,wheel1,wheel2,wheel3,wheel4):
    self.wheel1 = wheel1
    self.wheel2 = wheel2
    self.wheel3 = wheel3
    self.wheel4 = wheel4

```

## File I/O

- **my_file = open("file.txt","r")** - r = read, w = write, r+ = both
- **print my_file.readline()** => returns first line
  - **print my_file.readline()** => returns next line
- **my_file.close()** - important when done with file
- **my_file.closed** - returns if file is closed
- **write sth to a file:**
```PYTHON
with open("file.txt","w") as textfile:
  textfile.write("string")
```
