# Moving Data

##### how to move data in cpu , memory and register :

<p>mov is most frequently used instruction in assemlby.</p>
<p>Usage Format:</p>

		MOVx source,destination

<p>there are three variation of mov based upon size of source and destination.</p>

- movl = moves 32 bit value
		movl %eax, %ebx

- movw = moves 16 bit value
		movw %ax, %bx

- movb = moves a 8 bit value
		movb %ah, %bh

##### various ways data trasfer might happen.

1. between registers :
		movl %eax, %ebx

2. between registers and memory :
		num_label:
			.int 10

		movl %eax, num_label
		movl num_label, %ebx

3. immediate value into register
		# it moves value 10 in ebx
		movl $10, %ebx

4. immediate value into memory location :
		locaton:
			.byte 0
		movb $10, location

5. moving data into an indexed memory location :
		IntegerArray:
			.int 10,20,30,40,50
		movl %eax, IntegerArray(0,2,4)


##### Indirect addressing using registers

if we put `$` sign before the label, then we take memory address of the variable and not the value

		movl $my_number,%edi

in above instruction we do not move value of `my_number` to `%edi` instead we move address location of `my_number` to `%edi`

		# place value "9" in memory locaiton pointed to by %edi
		movl $9,(%edi)

		#place value "9" in memory location pointed by (%edi + 4)
		movl $9,4(%edi)

		#place value "9" in memory location pointed by (%edi -2)
		movl $9,-2(%edi)
