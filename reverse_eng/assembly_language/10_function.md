# Functions

- Defining a function on assembly :

		.type Function_name, @function
		Function_name:
			code
			code
			ret

- function is invoked by using `call Function_name`

- passing arguments to functions
	1. registers
	2. global memory location
	3. stack

- returining value from a functions
	1. register
	2. global memory locations.


* *Passing argument to func by register*

		.data 

			HelloWorld:
				.asciz "Hello World

			HelloFunction:
				.asciz "Hello Function

		.text 

		.globl _start

		.type MyFunction, @function

		MyFunction:	# String pointer and len 	to be added by caller 

				movl $4, %eax
				movl $1, %ebx
				int $0x80
				ret 

		_start :
			nop
			# Print the Hello World String 
		
			leal HelloWorld, %ecx
			movl $14, %edx 
			call MyFunction

			# Print Hello Function 

			leal HelloFunction, %ecx
			movl $17, %edx
			call MyFunction

			# Exit Routine 
		
		ExitCall:
			movl $1, %eax
			movl $0, %ebx 
			int $0x80 


* *Passing argument to function by global memory location*


```asm
.data 

	HelloWorld:
		.asciz "Hello World!\n"

	HelloFunction:
		.asciz "Hello Function!\n"

.bss 
	.lcomm StringPointer, 4
	.lcomm StringLength, 4

.text 

	.globl _start

	.type MyFunction, @function

	MyFunction:	# String pointer and len to be added by caller 

			movl $4, %eax
			movl $1, %ebx
			movl StringPointer, %ecx
			movl StringLength, %edx
			int $0x80
			ret 

	_start :
		nop

		# Print the Hello World String 
		movl $HelloWorld, StringPointer
		movl $14, StringLength	
		call MyFunction

		# Print Hello Function 
		movl $HelloFunction, StringPointer
		movl $17, StringLength 
		call MyFunction

		# Exit Routine 
		
	ExitCall:
		movl $1, %eax
		movl $0, %ebx 
		int $0x80 
```