# Importation


    import bitLogic
            

- it is a default module so it does not requie full filepath

# Usage
- bitLogic module provides bit by bit logic for binary number

# Provided functions
- bitNot
	- negates every bit in the number provided, and returns it

          binNumber = bx0010011
          negatedBinNumber = bitNot(binNumber)
          # returns bx11011 (lenght is reduced because the two MSB turn to 0) #

- bitAnd
	- receives two operands, and executes a bit by bit and between them
	- if the two numbers have a different size, the missing bits on the smallest number are considered as 0

          leftBinNumber = bx0010011
          rightBinNumber = bx01011

          anded = bitAnd(leftBinNumber, rightBinNumber)
          # returns bx0 because the two numbers have no common bit at 1 #
	
	- truth table:


          | right |  left | output |
          |-------|-------|--------|
          |    0  |   0   |    0   |
          |    0  |   1   |    0   |
          |    1  |   0   |    0   |
          |    1  |   1   |    1   |

- bitNand
	- receives two operands, and execures a bit by bit nand between them
	- if the two numbers have different size, the missing bits on the smallest number are considered as 0

          leftBinNumber =  bx0010011
          rightBinNumber = bx01011

          anded = bitNand(leftBinNumber, rightBinNumber)
          # returns bx1111111 #
	
	- truth table:

          | right |  left | output |
          |-------|-------|--------|
          |    0  |   0   |    1   |
          |    0  |   1   |    1   |
          |    1  |   0   |    1   |
          |    1  |   1   |    0   |
- bitOr
	- receives two operands, and execures a bit by bit or between them
	- if the two numbers have different size, the missing bits on the smallest number are considered as 0

          leftBinNumber =  bx0010011
          rightBinNumber = bx01011

          anded = bitOr(leftBinNumber, rightBinNumber)
          # returns bx0111111 #
	
	- truth table:


          | right |  left | output |
          |-------|-------|--------|
          |    0  |   0   |    0   |
          |    0  |   1   |    1   |
          |    1  |   0   |    1   |
          |    1  |   1   |    1   |
- bitNor
	- receives two operands, and execures a bit by bit nor between them
	- if the two numbers have different size, the missing bits on the smallest number are considered as 0

          leftBinNumber =  bx0010011
          rightBinNumber = bx01011

          anded = bitNor(leftBinNumber, rightBinNumber)
          # returns bx1 #

	- truth table:

          | right |  left | output |
          |-------|-------|--------|
          |    0  |   0   |    1   |
          |    0  |   1   |    0   |
          |    1  |   0   |    0   |
          |    1  |   1   |    0   |
- bitXor
	- receives two operands, and execures a bit by bit xor between them
	- if the two numbers have different size, the missing bits on the smallest number are considered as 0

          leftBinNumber =  bx0010011
          rightBinNumber = bx01101

          anded = bitXor(leftBinNumber, rightBinNumber)
          # returns bx0100111 #

	- truth table:
	
          | right |  left | output |
          |-------|-------|--------|
          |    0  |   0   |    0   |
          |    0  |   1   |    1   |
          |    1  |   0   |    1   |
          |    1  |   1   |    0   |
- bitXnor
	- receives two operands, and execures a bit by bit xnor between them
	- if the two numbers have different size, the missing bits on the smallest number are considered as 0

          leftBinNumber =  bx0010011
          rightBinNumber = bx01101

          anded = bitXnor(leftBinNumber, rightBinNumber)
          # returns bx101 #

	- truth table:

          | right |  left | output |
          |-------|-------|--------|
          |    0  |   0   |    1   |
          |    0  |   1   |    0   |
          |    1  |   0   |    0   |
          |    1  |   1   |    1   |
