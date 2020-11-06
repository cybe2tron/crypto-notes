# Conditional branching

This is performed by a set of jump instructions j`condition` depending upon the condition.

eg: JXX - JA,JAE,JE,JG,JZ,JNZ ...etc

whether a conditional jump happen or not is dicatated by the state of the various flag in the EFLAG register.

	zero flag(zf)
	parity flag(pf)
	overflow flag(of)
	sign flag(sf)
	carry flag(cf)

to use conditional jumps you must have an operation which sets the EFLAGS register appropriately.

in conditional jumps - onlly short and near jumps are supported . Far jumps are not suppoerted.

Example (jz flag)

	.data 
	
	HelloWorld:
		.asciz "Hello World!\n"

	ZeroFlagSet:
		.asciz	"Zero Flag was Set!"

	ZeroFlagNotSet:
		.asciz  "Zero Flag Not Set!"


	.text 

	.globl _start

	_start:

		nop	
		movl $10, %eax
		jz FlagSetPrint

	FlagNotSetPrint:
		movl $4, %eax
		movl $1, %ebx
		leal ZeroFlagNotSet, %ecx
		movl $19, %edx
		int $0x80 
		jmp ExitCall



	FlagSetPrint:
		movl $4, %eax
		movl $1, %ebx
		leal ZeroFlagSet, %ecx
		movl $19, %edx
		int $0x80 
		jmp ExitCall


	ExitCall:
		movl $1, %eax
		movl $0, %ebx
		int $0x80 

	PrintHelloWorld:
		
		movl $4, %eax
		movl $1, %ebx
		leal HelloWorld, %ecx
		movl $14, %edx
		int $0x80
		jmp ExitCall

in the above program if the jz flag is set then it will jump to `FlagSetPrint` function.(in our case we didnt set it.) and if we did't set it then it does not change program execution flow and `FlagNotSetPrint` is executed and program exits.

if we set zf (by using `xorl %eax, %eax`) above the `jz FlagSetPrint` intruction the jz flag is set and program jump to `FlagSetPrint`.


**LOOP Instruction**

it help us to execute set of instruction for a predetermined number of times.
	this number is stored in `ECX`

loop automatically decrement `ECX` after every run.

Example:

	PrintHelloWorld:
    movl $10, %ecx
    PrintTenTimes:
        pushl %ecx
        movl $4, %eax
        movl $1, %ebx
        leal HelloWorld, %ecx
        movl $14, %edx
        int $0x80
        popl %ecx
    loop PrintTenTimes
    jmp ExitCall


`movl $10, %ecx` : it tells how many times loop executes.

`pushl %ecx` : while we push the `HelloWorld` address in `%ecx` the value 10 will be overwrite and loop execute indifinetly, to avoid this we save the value of `%ecx` by this cmd.

`popl %ecx` : restore the value of `%ecx`

 