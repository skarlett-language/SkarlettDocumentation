# General advice
### When operating with negative numbers, you are required to wrap them in parentheses. Skarlett's syntax does not allow an operator next to another

Example:
- do this

```	
a = 64 + (- 32)
```
- do NOT do this


```
a = 64 + -32
```
---

# Types and declarations
### Numbers
- int
    - base 10 integer numbers
    - includes "infinity"
	
```	
intVariable = 32
infinityVariable = inf
```

- float
    - base 10 numbers with a fractional part

```
floatVariable = 128.64
```

- hexa
	- base 16 integer numbers
	- it is required to put `hx` before the digits, to tell the interpreter that you are declaring a hexadecimal number

```
hexaVariable = hxF1
```

- binary
    - base 2 numbers
    - the compiler itself considers all binary numbers as integers, but you can use them also in two complement form, or IEEE 754
      - math in two complement must be user defined
    - it is required to put `bx` before the digits, to tell the interpreter that you are declaring a binary number
    - the MSB is at the extreme left position, while the LSB is at the extreme right
    - the use of any logic gate (explained later) between two binary numbers results in a bitwise operation, which returns a binary number, instead of a boolean one  

```
binaryVariable = bx1101011
```

### Strings
- combination of letters, numbers and symbols
- in Skarlett there are only single quoted strings

```
stringVariable = 'This is a string!'
```
- the "+" operator adds the provided string or char to the existing string
- the "*" operator repeats the string itself as many times as specified
  - the "+=" and "*=" operators do the same thing, but storing the value in the variable at the left of the operator

### List
- multi-type lists
- must be initialised as empty
- to add elements to the list, use the "+=" operator

```
listVariable = []
```

### Bool
- boolean values: "true" and "false"

```
boolVariable = true
```

### Null
- null type

```
nullVariable = null
```

### Hash table
- hash tables need to be declared empty, at first, then you will be able to insert elements
- the declaration consists in using the "hash" keyword
```
myHash = hash
```
- to add elements, you must use the "set()" builtin function
- to get elements, use the "get()" builtin function 

---

# Operators
### Logic
- standard operators
	- like any other language, Skarlett provides the standard logic operators
	- every operator requires two operands

```
==
!=
>
<
>=
<=	
```

- logic gates
    - Skarlett contains the builtin implementation of all the logic gates
    - logic gates used between binary numbers trigger bitwise logic

```
not
		| input | output |
		|-------|--------|
		|   0   |    1   |
		|   1   |    0   |

and 
		| input1 input2 | output |
		|---------------|--------|
		|    0      0   |    0   |
		|    0      1   |    0   |
		|    1      0   |    0   |
		|    1      1   |    1   |

nand (not and)
		| input1 input2 | output |
		|---------------|--------|
		|    0      0   |    1   |
		|    0      1   |    1   |
		|    1      0   |    1   |
		|    1      1   |    0   |

or 
		| input1 input2 | output |
		|---------------|--------|
		|    0      0   |    0   |
		|    0      1   |    1   |
		|    1      0   |    1   |
		|    1      1   |    1   |

nor (not or)
		| input1 input2 | output |
		|---------------|--------|
		|    0      0   |    1   |
		|    0      1   |    0   |
		|    1      0   |    0   |
		|    1      1   |    0   |

xor 
		| input1 input2 | output |
		|---------------|--------|
		|    0      0   |    0   |
		|    0      1   |    1   |
		|    1      0   |    1   |
		|    1      1   |    0   |

xnor (not xor)
		| input1 input2 | output |
		|---------------|--------|
		|    0      0   |    1   |
		|    0      1   |    0   |
		|    1      0   |    0   |
		|    1      1   |    1   |


in the truth tables, "1" represents true, and "0" represents false
```
### Arithmetic
- arithmetic operators require two operands, and are able to make multi-type math

```
+     (sum)
-     (subtraction)
*     (multiplication)
/     (division)
%     (module)
**    (power)
//    (integer division)
>>    (right shift)
<<    (left shift)
```

- every operator has his own assignment form, for arithmetic variable overwriting

```
+= 
-=
*=
/=
%=
**=
//=
>>=
<<=
```
	
### Square bracket getter
- square bracket getter is a standard operator which allows to take an element from a list, a string, a binary number
- needs an integer number as parameter

```
example = bx0010011
example[3] (returns 1)
```
---

# Comments
## Single line
- single line comments are made putting `#!` before the comment

```
#! single line comment
```

## Multi Line
- multi line comments require the `#` symbol to be at the beginning and end of the comment

```
# this is 
a multi-line
comment #
```
---

# Conditionals
- conditional statements involve three keywords:
	- `if` 
		- requires a condition
		- its condition is the first to be checked
	- `elif` 
		- requires a condition
		- its condition is checked only if the `if` condition evaluates to `false`
		- multiple `elif` can coexist in the same statement, and their condition is verified in the order with which they are written
	- `else`
		- can't have a condition
		- its statement is executed only if the `if` and eventual `elif` conditions evaluate to `false`
- every statement needs to be wrapped around with curly brackets
- condition do not require parentheses wrapping, but it can be used

```
if 5 > 8 {
    # if statement #

} elif 5 < 8 {
    # elif statement #

} else {
    # else statement #
}
```
---

# Loops
- Skarlett implements while loops, from loops, do-until loops and for loops
- every loop requires a condition
- its statement need to be wrapped around with curly brackets
- in loop's statements there are two keywords to alter the normal execution flow
	- `exit`
		- stops the execution of the loop statement and exits the loops
	- `continue`
		- skips to the next iteration

### While loop example
```
i = 0
while i < 10 {
    # do something #
    if i == 6 {
        i += 2
        continue
    } elif i == 8 {
        exit
    }
    i += 1
}
```
- the loop's condition gets verified before every iteration, 
and only if the condition evaluates to true, the statement is executed

### From loop example
```
from i = 100 to 5 step -2 {
    stdout(i)
}
```
- from loops implement new keywords:
  - `from` -> tells the interpreter the initialisation of a From Loop
  - `to` -> after the iteration variable declaration, it is required to use the `to` keyword in order to tell the interpreter the final value for the iteration
  - `step` -> if not specified, step is considered to be "1", otherwise, the iteration variable will be incremented or decremented accordingly to the `step` value

### Do-Until loops
```
i = 0
do {
    stdout(i)
    i += 1
} until i == 10
```
- do-until loops implements its keywords:
  - `do` -> initialises the loop
  - `until` -> after which there must be the condition
- do-until loops work in negative logic, which means that the loop will end when the provided condition evaluates to "true"
- the statement of the loop gets executed before the condition is verified, at every iteration
  - the execution of the statement is granted at least one time

### For loops
```
var = bx10100

for bit in var {
    stdout(var)
}
```
- for loops only work with iterable types, which are lists, strings and binary numbers
- the iteration variable (in the example "bit") can have any name you like, except keywords, and is self-declared and assigned at execution time

---

# Function declaration
- function declaration requires at first the "fnc" keyword, to tell the interpreter that you are declaring a new function
- parameters must be declared within rounded brackets, and separated by a ","
	- parameters can be values, variables and functions
		- to call a function passed as parameter, just put "()" after the alias and give it its eventual parameters
- the function's statement must be wrapper around with curly brackets
- every function has "null" default return type
- to return something, you can use the "return" keyword
	- remember to return only one variable or value
	- to return multiple values, you can put them in a list and return the list

```
fnc greet(name) {
    returnString = 'Hi ' + name + '! Welcome to Skarlett!'
    return returnString
}
```
---

# Builtin functions
- the following is a list of all the builtin functions in Skarlett, with relative explanation and usage example

### Casting functions
- convert a value in the desired type, if possible

```
int()
float()
hexa()
bin()
string()
bool()
```

- every function takes one parameter, and return the casted value

```
originalValue = 32
intValue = int(originalValue)       # returns 32 #
hexaValue = hexa(originalValue)     # returns hx20 #
binValue = bin(originalValue)       # returns bx100000 #
stringValue = string(originalValue) # returns '32' #
boolValue = bool(originalValue)     # returns true #
floatValue = float(originalValue)   # returns 32.0 #
```

### Input and output
- output
  - `stdout` -> prints to the argument to the standard output 
  - `stderr` -> prints the argument to the standard error output
- input
  - `stdin` -> returns the value from the standard input, printing the prompt passed as argument before the input retrieval
  - `stdpipe` -> returns the value from the standard pipe, useful for command combination in linux
    - e.g. `ls -l | skarlett myFile.skt`
  - `stdargs` -> reads the arguments given in the terminal, and returns it as a list
    - e.g. `skarlett myFile.skt arg1 arg2 arg3`
  
### Type
- returns the type of the provided value or variable in string form

```
value = 32
type(value)    # returns 'int' #
type(hxF1)     # returns 'hexanumber' #
```

### Split and join
- there is a double implementation of each method
	- the normal one (used on strings and lists)
	- the binary one (used only on binary numbers)
- split
	- the normal version received a string and a target, basing on which it will return a list containing the separated elements
	- the binary version only receives the binary number, and returns a list of 0 and 1 in int form
- join
	- the normal version takes a list and a separator, and returns a string containing each value in the list, separated by the separator
	- the binary version only takes a list of zeros and ones and returns a binary number, which digits correspond to the list


```	
stringVar = 'This is a string'
splitted = split(stringVar, ' ') # returns ['This', 'is', 'a', 'string'] #

binaryVar = bx10011
bits = binSplit(binaryVar)      # returns [1, 0, 0, 1, 1]

joinedString = join(splitted, ' ! ') # returns 'This ! is ! a ! string !' #

joinedBits = binJoin(bits)       # returns bx10011 #
```

### Fragment
- function which receives a string, list or binary number, and returns a fragment of it
- as parameters, together with the value or variable, it requires two integers, which indicated the beginning index and the ending index for the "cut"

```
fragment('Skarlett', 1, 4)     # returns 'karl' #
fragment(bx0010011, 2, 5)      # returns bx1001 #
```

### Trim
- takes a string as an input
- returns the string after removing blank spaces (' '), tabs ('\t') and new lines ('\n') before and after the string 

```
trim('      this is a string  \t\t\t  ')    # returns 'this is a tring' #
```

### Find
- takes as inputy an iterable (such as string, list, binarynumber) and an element that may be contained, and searches it
- in case of success, returns the index of the searched element, otherwise -1

```
find(myList, 'stringToSearch')
```

### Remove
- takes as input a list and an index (in form of int, hexanumber or binarynumber)
- returns the removed element

```
remove(myList, 3)
```

### File input/output
- ##### Read
  - takes as input the file path
  - returns the content of the file, if readable

```
readFile('myFile.txt')
```
- ##### Write
  - takes as input the file path and the content to write on it

```
writeOnFile('myFile.txt', 'this is the new content')
```

### Set index
- takes as input a list, an index (in form of a integer, binarynumber or hexanumber) and a value (in any form)
- puts the value in the list at the specified index

```
setIndex(myList, 4, hxF1)
```

### Sleep
- takes as input any type of number, and waits the corresponding time
- the argument number represents seconds

```
sleep(bx001)
```

### Time stamp
- takes not argument
- returns a float representing the current time stamp, which can be used to determine time deltas (e.g. execution time)

``` 
before = timeStamp()
# Here goes the code #
after = timeStamp()

stdout('Elapsed time: ' + (after - before))
```

### Round
- takes as input:
  - a float, which will be rounded
  - a number (int, hexa, binary) representing the number of digits after the comma to which round up

```
round(1.4142135623, hx4)        # returns 1.4142 #
```

### Set & Get
- builtin fuctions to be used to interact with hash tables
- `set(table, key, value)`
  - requires three parameters: the hash table, the key you want to use and the value to be hashed
```
set(myHash, 'myKey', 'myValue')
```
- `get(table, key)` 
  - requires two parameters: the hash table and the key to be returned
  - if the key cannot be found, "null" is returned
---

# Importation
- importation requires the file path (relative or absolute) of the module to import
```
import '/home/user/skarlettCode/myModule.skt'
```

- to use functions and variables coming from a module, it is required to put `<moduleName>::` before
- the module's file name sets the module's name itself
```
var = myModule::moduleVariable

myModule::moduleFunction()
```

---

# Keywords
- the following is the list of all Skarlett's keywords:
  - `if`
  - `elif`
  - `else`
  - `while`
  - `from`
  - `to`
  - `step`
  - `do`
  - `until`
  - `for`
  - `in`
  - `continue`
  - `exit`
  - `fnc`
  - `return`
  - `hash`
  - `not`
  - `and`
  - `nand`
  - `or`
  - `nor`
  - `xor`
  - `xnor`
  - `import`
