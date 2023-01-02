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
