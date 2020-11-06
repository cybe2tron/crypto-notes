# Unconditional Branching

* **JMP**
	1. compare it with GOTO:statement in C
	2. syntax -`JMP Label`
	3. short,Near and Far jump possible 

short : +128 or - 128 bytes from the current location in the instruction region.

far : jmp to different segment whenever you are in segmented memory module.

near : both of them

Example Of `JMP` statement:

		.data
			HelloWorld:
				.ascii "Hello World"
			callDemo:
				.ascii "call works"

		.text

			.global _start

			_start:

			jmp callMe
			#write hello world in console
			movl $4, %eax
			movl $1, %ebx
			movl $HelloWorld, %ecx
			movl $12, %edx
			int $0x80

		ExitProgram:
			#exit the program
			movl $1, %eax
			movl $10, $ebx
			int $0x80

		callMe:
			movl $4, %eax
			movl $1, %ebx
			movl $callDemo, %ecx
			movl $11, %edx
			int $0x80
			ret

in above example when we jmp ,then `eip` points to the callMe function.

* **CALL**
	1. just calling a function
	2. syntax : `call locataion`
	3. there is an associated `RET` statement with every call.
		1. compare it with `return` statement in C

Example :

		.data
			HelloWorld:
				.ascii "Hello World"
			callDemo:
				.ascii "call works"

		.text

			.global _start

			_start:

			call callMe
			#write hello world in console
			movl $4, %eax
			movl $1, %ebx
			movl $HelloWorld, %ecx
			movl $12, %edx
			int $0x80

		ExitProgram:
			#exit the program
			movl $1, %eax
			movl $10, $ebx
			int $0x80

		callMe:
			movl $4, %eax
			movl $1, %ebx
			movl $callDemo, %ecx
			movl $11, %edx
			int $0x80
			ret

