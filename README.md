# Summary
- [Types and declarations](https://github.com/cpy-dev/lang/tree/master#types-and-declarations)
    - [Numbers](https://github.com/cpy-dev/lang/tree/master#numbers)
      - [Negative numbers](https://github.com/cpy-dev/lang/tree/master#negative-numbers)
    - [Strings](https://github.com/cpy-dev/lang/tree/master#strings)
    - [List](https://github.com/cpy-dev/lang/tree/master#lists)
    - [Bool](https://github.com/cpy-dev/lang/tree/master#bool)
    - [Null](https://github.com/cpy-dev/lang/tree/master#null)
- [Operators](https://github.com/cpy-dev/lang/tree/master#operators)
    - [Logic](https://github.com/cpy-dev/lang/tree/master#logic)
    - [Arithmetic](https://github.com/cpy-dev/lang/tree/master#arithmetic)
- [Comments](https://github.com/cpy-dev/lang/tree/master#comments)
- [Conditionals](https://github.com/cpy-dev/lang/tree/master#conditionals)
- [Loops](https://github.com/cpy-dev/lang/tree/master#loops)
- [Function declaration](https://github.com/cpy-dev/lang/tree/master#function-declaration)
- [Builtin functions](https://github.com/cpy-dev/lang/tree/master#builtin-functions)
    - [Casting functions](https://github.com/cpy-dev/lang/tree/master#casting-functions)
    - [Input and output](https://github.com/cpy-dev/lang/tree/master#input-and-output)
    - [Type](https://github.com/cpy-dev/lang/tree/master#type)
    - [Split and join](https://github.com/cpy-dev/lang/tree/master#split-and-join)
    - [Fragment](https://github.com/cpy-dev/lang/tree/master#fragment)
- [Importation](https://github.com/cpy-dev/lang/tree/master#importation)
- [Standard modules](https://github.com/cpy-dev/lang/tree/master#standard-modules)

---

# General advice
### In Skarlett, spaces are very important, remember to always put them between variables, functions, operators and keywords. Brackets are the onbly which do not require space-separation rule.

Example:
- do this
	

	a = 32 + 64
	
- do NOT do this


	a=32+64

### Wrap with parentheses the operations which are nested inside others, in case they have different nature

Example:
-  do this


	if ((a + b) > 0) and ((b + c) != 100)
	
- do NOT do this


	if a + b > 0 and b + c != 100

### When operating with negative numbers, you are required to wrap them in parentheses. Skarlett's syntax dows not allow an operator next to another

Example:
- do this

	
    a = 64 + (- 32)

- do NOT do this


	a = 64 + -32
---

# Types and declarations
### Numbers
- int
    - base 10 integer numbers
    - includes "infinity"
	
	
	intVariable = 32
	infinityVariable = inf


- float
    - base 10 numbers with a fractional part


	floatVariable = 128.64


- hexa
	- base 16 integer numbers
	- it is required to put "hx" before the digits, to tell the interpreter that you are declaring a hexadecimal number


	hexaVariable = hxF1


- binary
    - base 2 numbers
    - the compiler itself considers all binary numbers as integers, but you can use them also in two complement form, or IEEE 754
        - in this case, remember that to use math on them, you have to call the "bitMath" builtin module
    - it is requierd to put "bx" before the digits, to tell the interpreter that you are declaring a binary number
    - the LSB is at the extreme left position, while the MSB is a the extreme right


	binaryVariable = bx0010011

#### Negative numbers
- only int and float can have a negative value
- if another type of number is declared as negative, its type will be converted to int or float
- example:


	negativeNumber = -hxF1

	show(negativeNumber) 		# prints: -241 #
	show(type(negativeNumber)) 	# prints: int #

### Strings
- combination of letters, numbers and symbols
- in Skarlett there are only single quoted strings


	stringVariable = 'This is a string!'

- the "+" operator adds the provided string or char to the existing string
- the "*" operator repeats the string itself as many times as specified
  - the "+=" and "*=" operators do the same thing, but storing the value in the variable at the left of the operator

### List
- multi-type lists
- must be initialised as empty
- to add elements to the list, use the "+=" operator


	listVariable = []


### Bool
- boolean values: "true" and "false"


	boolVariable = true


### Null
- null type


	nullVariable = null

---

# Operators
### Logic
- standard operators
	- like any other language, Skarlett provides the standard logic operators
	- every operator requires two operands


	==
	!=
	>
	<
	>=
	<=	
	

- logic gates
    - Skarlett contains the builtin implementation of all the logic gates


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

### Arithmetic
- arithmetic operators require two operands, and are able to make multi-type math


	+     (sum)
	-     (subtraction)
	*     (multiplication)
	/     (division)
	%     (module)
	**    (power)
	//    (integer division)
	>>	  (right shift)
	<<    (left shift)


- every operator has his own assignment form, for arithmetic vriable overwriting


	+= 
	-=
	*=
	/=
	%=
	**=
	//=
	>>=
	<<=

	
### Square bracket getter
- square bracket getter is a standard operator which allows to take an elemet from a list, a string or a binary number
- needs an integer number as parameter


	example = bx0010011
	example[3] (returns 1)

---

# Comments
- comments require the "#" symbols, which has to be placed at the beginning and at the end of the comment
- multi-line comments are allowed


	# this is 
	a multi-line
	comment #

---

# Conditionals
- conditional statements involve three keywords:
	- if 
		- requires a condition
		- its condition is the first to be checked
	- elif 
		- requires a condition
		- its condition is checked only if the "if" condition is false
		- multiple "elif" can coexist in the same statement, and their condition is verified in the order with which they were written
	- else
		- can't have a condition
		- its statement is executed only if the "if" and eventual "elif" condition are false
- every statement needs to be wrapper around with curly brackets
- condition do not require parentheses wrapping, but it canbe used


	if 5 > 8 {
		# if statement #
	} elif 5 < 8 {
		# elif statement #
	} else {
		# else statement #
	}

---

# Loops
- Skarlett only implements while loops
- every loop require a condition
- its statement need to be wrapped around with curly brackets
- in loop's statements there are two keywords to alterate the normal execution flow
	- exit
		- stops the execution of the loop statement and exits the loops
	- continue
		- skips to the next condition check


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


	fnc greet(name) {
		returnString = 'Hi ' + name + '! Welcome to Skarlett!'
		return returnString
	}

---

# Builtin functions
- the following is a list of all the builtin functions in Skarlett, with relative explanation and usage example
### Casting functions
- convert a value in the desider type, if posible

 
	int()
	float()
	hexa()
	bin()
	string()
	bool()


- every function takes one parameter, and return the casted value


    originalValue = 32
    intValue = int(originalValue)       # returns 32 #
    hexaValue = hexa(originalValue)     # returns hx20 #
    binValue = bin(originalValue)       # returns bx000001 #
    stringValue = string(originalValue) # returns '32' #
	boolValue = bool(originalValue)     # returns true #
	floatValue = float(originalValue)   # returns 32.0 #


### Input and output
- show function
	- prints in the console whathever it receives as parameter


	show('Skarlett!') # prints Skarlett! to the console #


- get function
	- gets text typed from the console and returns it
	- can receive a parameter, which is printed before the typing detection


	get('Type your name: ')     # prints "Type your name: " and waits for you to type something and press the "return" key #


### Type
- returns the type of the provided value or variable in sring form


	value = 32
	type(value)    # returns 'int' #
	type(hxF1)     # returns 'hexanumber' #


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


	stringVar = 'This is a string'
	splitted = split(stringVar, ' ') # returns ['This', 'is', 'a', 'string'] #

	binaryVar = bx0010011
	bits = binSplit(binaryVar)      # returns [0, 0, 1, 0, 0, 1, 1]

	joinedString = join(splitted, ' ! ') # returns 'This ! is ! a ! string !' #

	joinedBits = binJoin(bits)       # returns bx0010011 #


### Fragment
- function which receives a string, list or binary number, and returns a fragment of it
- as parameters, togeter with the value or variable, it requires two integers, which indicated the beginning index and the ending index for the "cut"


	fragment('Skarlett', 1, 4)     # returns 'karl' #
	fragment(bx0010011, 2, 5)      # returns bx1001 #


---

# Importation
- importation of files and modules has two forms:
	- standard modules importation
		- just require the "import" keyword and the name of the module
	- user defined modules or files importation
		- requires the "import" keyword and the full path of the file
		- the file path must be in string form, so in single quoted strings
		- remember to put the file extension ".skt" at the end of the file path


	import bitLogic
	import '/home/user/skarlettCode/myFile.skt'


---

# Standard modules
- down here there is the list of the standard modules provided with the language
- every module has his own documentation


	bitLogic
	bitMath

