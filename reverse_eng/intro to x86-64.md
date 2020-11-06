# Intro to x86-64

Computers execute machine code, which is encoded as bytes, to carry out tasks on a computer.

This machine is code is usually produced by a compiler, which takes the source code of a file, and after going through some intermediate stages, produces machine code that can be executed by a computer.


Intel first started out by building 16-bit instruction set, followed by 32 bit, after which they finally created 64 bit. All these instruction sets have been created for backward compatibility,

backward compatibility means 32 bit architecture will run on 64 bit machines.(but 64 bit can not run on 32 bit)


the source code is first compiled into assembly (.s file) , after which the assembler converts it into an objects program (.o file) and linker makes it executable.

# scrennshot assembly_sctruc

1. As we can see from above, the values on the complete left column are memory addresses of the instructions, and these are usually stored in a structure called the stack.

2. The middle column contains the instructions encoded in bytes(what is usually the machine code)

3. ast column actually contains the human readable instructions. 

assembly language involves using register to do following :

	1. transfer data between memory and register or vice versa

	2. perform artithmatic operations on register and data

	3. trasfer control to other parts of the program.


in architecture x86-64 , the register are 64 bit and intel has a list of 16 registers.


# screenshot 16_register

Even though the registers are 64 bit, meaning they can hold up to 64 bits of data, other parts of the registers can also be referenced. In this case, registers can also be referenced as 32 bit values as shown in above image. and registers can be referenced as 16 bit and 8 bit(higher 4 bit and lower 4 bit). 

the first 6 register are known as general purpose register.

the `%rsp` is stack pointer which to the top of the stack.

`%rbp` points to the currently being executed instruction.

* * * 

To move data using registers following instructions is used.

	MOVx source, destination

*This includes:*

1. Trasferring constant (prefixed by `$` ) eg : `movq $3 rax` would move the value 3 in rax register.

2. Transferring value from a register. eg : `movq %rax, %rbx` which move value from rax to rbx.

3. Transfer value to memory address. eg :
`movq %rax, (%rbx)` which move value in rax to the memory address pointed by rbx


the x represent the size of data.

data tyep | suffix | size
----------|--------|------
bytes | b | 1
word | w | 2
Double word | l | 4
Quad word | q | 8
single precision | s | 4
Double precision | l | 8


When dealing with memory manipulation using registers, there are other cases to be considered:

    (Rb, Ri) = MemoryLocation[Rb + Ri]

    D(Rb, Ri) = MemoryLocation[Rb + Ri + D]

    (Rb, Ri, S) = MemoryLocation(Rb + S * Ri]

    D(Rb, Ri, S) = MemoryLocation[Rb + S * Ri + D]


**some other important instruction**

`leaq source, destination` : this instruction sets destination to the address denoted by the expression in source

`addq source, destination`: destination = destination + source

`subq source, destination`: destination = destination - source

`imulq source, destination`: destination = destination * source

`salq source, destination`: destination = destination << source where << is the left bit shifting operator

`sarq source, destination`: destination = destination >> source where >> is the right bit shifting operator

`xorq source, destination`: destination = destination XOR source

`andq source, destination`: destination = destination & source

`orq source, destination`: destination = destination | source

***

**if statement**

Conditional execution in assembly language is accomplished by several looping and branching instructions. These instructions can change the flow of control in a program. Conditional execution is observed in two scenarios

1. Unconditional jump :

this is performed by `jmp` instruction. this instruction transfer control to the address of an instruction that does not follow the currently execution instruction.

2. Conditional jump: 

This is performed by a set of jump instructions `j<condition>` depending upon the condition.

*CMP instruction*

its compare two operands and generally used in conditional execution.This instruction basically subtracts one operand from the other for comparing whether the operands are equal or not

`cmp destination, source`

The destination operand could be either in register or in memory. The source operand could be a constant (immediate) data, register or memory.

*Example:*

```asm
CMP DX,	00  ; Compare the DX value with zero
JE  L7      ; If yes, then jump to label L7
.
.
L7: ...
```

**conditional jump**

If some specified condition is satisfied in conditional jump, the control flow is transferred to a target instruction.

Following are the conditional jump instructions used on signed data used for arithmetic operations −

Instruction |	Description |	Flags tested
------------|---------------|----------------
JE/JZ |	Jump Equal or Jump Zero |	ZF
JNE/JNZ |	Jump not Equal or Jump Not Zero |	ZF
JG/JNLE |	Jump Greater or Jump Not Less/Equal |	OF, SF, ZF
JGE/JNL |	Jump Greater/Equal or Jump Not Less |	OF, SF
JL/JNGE |	Jump Less or Jump Not Greater/Equal |	OF, SF
JLE/JNG |	Jump Less/Equal or Jump Not Greater |	OF, SF, ZF


Following are the conditional jump instructions used on unsigned data used for logical operations −

Instruction |	Description |	Flags tested 
------------|---------------|-----------------
JE/JZ |	Jump Equal or Jump Zero |	ZF
JNE/JNZ |	Jump not Equal or Jump Not Zero |	ZF
JA/JNBE |	Jump Above or Jump Not Below/Equal| 	CF, ZF
JAE/JNB |	Jump Above/Equal or Jump Not Below |	CF
JB/JNAE |	Jump Below or Jump Not Above/Equal |	CF
JBE/JNA |	Jump Below/Equal or Jump Not Above |	AF, CF

The following conditional jump instructions have special uses and check the value of flags −

Instruction |	Description |	Flags tested
-------------|---------------|--------------
JXCZ |	Jump if CX is Zero |	none
JC |	Jump If Carry |	CF
JNC |	Jump If No Carry |	CF
JO 	|Jump If Overflow 	|OF
JNO |	Jump If No Overflow |	OF
JP/JPE |	Jump Parity or Jump Parity Even |	PF
JNP/JPO |	Jump No Parity or Jump Parity Odd |	PF
JS 	|Jump Sign (negative value) |	SF
JNS |	Jump No Sign (positive value) |	SF


**loops**

