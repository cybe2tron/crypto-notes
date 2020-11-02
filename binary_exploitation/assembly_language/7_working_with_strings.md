# Working With Strings in Assembly

**moving strings from one memory to another.**

		MOVSx:
		MOVSB - move a byte(8 bits)
		MOVSW - move a word(16 bits)
		MOVSL - move a double word(32)

source - `ESI` points to memory location<br>
Destination - `EDI` points to memory locations.

		.data
			#here we take two strings
			string1:
				.ascii "hello_world"
			string2:
				.ascii "h3110"

		.bss
			.lcomm Destination1, 100
			.lcomm Destination2, 100

		.text
			.globl _start

			_start:
				#simple copying using movsb,movsw,movsl

				movl $string1, %esi
				movl $destination1, %edi

				movsb
				movsw
				movsl

1. in above example first we take two initialized string.
2. then we take two uninitialized variable(in.bss segment)
3. then we copy address to `string1 ==> esi` and `destination ==> edi`
4. movsb : copy only one byte which will be `h`<br>

movsw : copy two byte which will be `el`<br>
movsl : copy four byte which will be `lo_wo`

##### The DF flag

Direction flag(DF) part of EFALGS register

Decides whether to increment / decrement ESI,EDI registers after a MOVSx instruction

if DF is set "1" => ESI,EDI registers are decrement</br>
if DF is set "0" => ESI, EDI are  incremented.

we can set DF using STD intruction<br>
we can clear DF using CLD instruction.

##### REP instruction

what happen if we want to move large string.becasue of movsb,movsw,movsl only move 8,16 and 32 bit, its studpid to call this function many times. here rep instruction comes to help.

- it used to repeat a string instruction over and over agina till the `ECX` register has a value >0

- how its work
	1. we load the ECX register with the string length
	2. use rep MOVSx instruction to copy the string from source to destination.
	3.  when each time movsx is executing ECX decrement its value and when its 0 its stop the transfer.

*Example*

		#first move addr of source and destination to esi and edi
		movl $string1, $esi
		movl $destination, $edi

		# set the string length in ecx
		movl $11, %ecx
		cld #clear the DF
		rep movsb 
		std


**Loading string from memory to registers** 

for load string from memory to register we use `LODSx`

Loading Strings :

1. loads into the `EAX` register
2. String source pointed to by `ESI`

this both condition should always true while using LODSx.

		LODSx:
			LODSB => load a byte from memory location into AL
			LODSW => load a word from memory into AX
			LODSL => Load a double word from memory into EAX

- ESI is automatically incremented / decremented based on DF-flag after the LODSx instruction exectues.

Example: loading a string from memory into EAX register

		cld #we want esi to be incremented

		# then we load memory locatin of hello world string into esi
		leal string1, $esi #here lea is load effective address intruction and l stand for loading into double word.

		lodsb
		movb $0, %al 

**Storing string from Register into memory**

for store strings from register to memory we use `STOSx`

		STOSx :
			STOSB => store AL to memory
			STOSW => store AX to memory
			STOSL => store EAX to memory.

- for storing strings , has to :
1. stores into memory from `EAX`
2. `EDI` points to destination memory. 

`EDI` is incremented / decremented based on the DF flag after every STOSx instruction is executed.

Example : storing string from EAX to memory

		leal Destination1, %edi
		stosb
		stosw 
		stosl 


**Comparing Strings**

we compare two strings using `CMPSx`.

- ESI contains source string, EDI the Destination string.
- DF flag decides whether ESI/EDI are incremented/decremented.

		CMPSx:
			CMPSB =>compare byte value
			CMPSW =>compares word value
			CMPSL =>compares double word value.

- CMPSx subtrack the destination string from the source string and set the EFLAGS register appropriately.

		leal string1, %esi
		leal string2, %edi
		cmpsb 

