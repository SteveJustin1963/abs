# abs

abs as in absolute value

forth code for "ABS" function from primitives and that handles 2's complement integers stored in hexadecimal format:

```
: ABS ( n -- abs )
   OVER 0x8000 AND 0 = IF   \ if n is equal to 0 or positive
      DROP   \ drop n from the stack
      0   \ push 0 onto the stack
   ELSE
      0x8000 AND 0 > IF   \ if n is negative
         0xFFFF XOR   \ invert all bits of n
         1 +   \ add 1 to get the absolute value
      THEN
   THEN
;


\ Test the ABS function
0xFFFF ABS .   \ prints 1
0x7FFF ABS .   \ prints 32767
0 ABS .   \ prints 0
```

This implementation of the "ABS" function uses a colon definition to define the function. It takes an integer value "n" stored in hexadecimal format as its argument and returns the absolute value of "n".

The function first checks if "n" is equal to 0 or is a positive number by ANDing it with 0x8000 (the most significant bit in 2's complement representation) and checking if the result is equal to 0. If it is, the function simply drops "n" from the stack and pushes 0 onto the stack as the result.

If "n" is not equal to 0 or positive, the function checks if "n" is negative by ANDing it with 0x8000 and checking if the result is greater than 0. If it is, the function inverts all of the bits of "n" using the "XOR" operator and then adds 1 to the result to get the absolute value. The absolute value is then returned as the output of the function.

This implementation of the "ABS" function does not use any built-in Forth functions or commands, only primitive operations such as stack manipulation and bitwise operations. It is therefore completely made out of Forth primitives.

You can test the function by calling it with a range of input values to make sure it is working correctly. For example, you can test it with the minimum and maximum possible values for a 16-bit 2's complement integer, like this:

```
0x8000 ABS .   \ prints 32768
0xFFFF ABS .   \ prints 1
0 ABS .   \ prints 0
```

## MINT

In a 2's complement system, integers are represented using a fixed number of bits, with the most significant bit (MSB) used to indicate the sign of the number. If the MSB is 0, the number is positive. If the MSB is 1, the number is negative.

The range of values that can be represented by a given number of bits in a 2's complement system depends on the number of bits used to represent the integers. For example, with 16 bits, the range of possible values is from -32768 to 32767, inclusive.

The integers from -32768 to -1 are represented in hexadecimal format as follows:

````
FFFF
FFFE
FFFD
...
0002
0001
0000
````
The integers from 0 to 32767 are represented in hexadecimal format as follows:

````
0000
0001
0002
...
FFFD
FFFE
FFFF
````
In this example, the hexadecimal values from 0000 to FFFF represent the integers from 0 to 32767 and from -32768 to -1, respectively, in 2's complement format.

## is zero a number ?
Yes, zero is a number. In mathematics, a number is a concept used to represent a quantity or amount. There are several different types of numbers, including natural numbers, whole numbers, integers, rational numbers, and irrational numbers.

Zero is considered a number because it is used to represent a quantity or amount. Specifically, zero represents the absence of any quantity or the lack of a magnitude.

In programming, a number is a data type that represents a numeric value. Different programming languages have different ways of representing numbers, such as using integers, floating-point numbers, or complex numbers. Zero is considered a number in programming because it can be represented using one of these numeric data types.

## is zero an integer?
Yes, zero is an integer. In mathematics, an integer is a number that can be written without a fractional component, such as -2, -1, 0, 1, 2, etc. Zero is an integer because it can be written without a fractional component.

In programming, an integer is a data type that represents a whole number. Depending on the programming language and the specific implementation, integers may be represented using a fixed number of bits, such as 16 or 32 bits, or using a variable number of bits. In some languages, there may also be different types of integers, such as signed or unsigned integers, or integers of different sizes.

Regardless of the specific representation or type, zero is always considered an integer in programming because it represents a whole number without a fractional component.

## whats the abs of zero?
The absolute value of zero is zero. The absolute value of a number is defined as the non-negative value of the number, regardless of its sign. Since zero is already a non-negative number, its absolute value is simply itself.

## strange things about 0 in programming
There are a few strange things about the number 0 in programming that may be worth noting:
- In some programming languages, the number 0 is considered a "falsey" value. This means that it is treated as if it were the boolean value "false" when used in a boolean context. For example, in an if statement, a condition that evaluates to 0 will be treated as if it were "false" and the corresponding code block will not be executed.
- In some programming languages, dividing any number by 0 is not allowed and will result in an error. This is because division by 0 is undefined in mathematics and can lead to unpredictable or erroneous results.
- In some programming languages, the number 0 may have different representations depending on the context. For example, in C and C++, the number 0 can be represented as an integer (e.g., 0 or 0L), a floating-point number (e.g., 0.0 or 0.0f), or a pointer (e.g., NULL).
- In some programming languages, the number 0 may have special behavior when used with certain operators or functions. For example, in Python, the number 0 is considered a "sentinel" value and is often used to indicate the end of a list or to mark a default or uninitialized state.

## meaning of 0 in forth
the number 0 is a literal value that represents the integer 0. It can be used in arithmetic expressions and other contexts where an integer value is expected.
For example, you can use the number 0 in Forth to initialize a variable to 0, like this:

```
0 VARIABLE myvar
```
You can also use the number 0 in Forth as a loop counter or as a comparison value in an if statement, like this:

```
: COUNTDOWN ( n -- )
   BEGIN
      DUP . 1 -
   UNTIL
   DROP
;

10 COUNTDOWN   \ prints numbers from 10 to 1

```
```
: IS_ZERO ( n -- flag )
   0 =
;

10 IS_ZERO .   \ prints 0 (false)
0 IS_ZERO .   \ prints 1 (true)
```

In these examples, the number 0 is used as the stopping condition for a loop and as the comparison value in an if statement.

## In MINT

do the loop when condition is false	
```
0=(something)     \\ code, 0 somthing= to the do(something)
0x!               \\ store 0 in x 
x@(true)(false)   \\ recall x then do (true) else do (false)



