# Gdb Usage Primer

 - `gdb ./program_name` : load program in gdb

 - `list 1` :list actual source code  (starting code listing from line 1)

 - `run para1 para2 ..`: run program

 - `disassemble <name of the function to disassemble` : disassemble program and dump assembly code

 - `break 8` : set breakpoint at line 8

 - `info registers` : dump all info of registers

 - `x/FMT` : to view to stack in memory locations.

 		how format (FMT) write :
 		x/10xw memory_location
 		10 : unit which display from memory_locatoin.
 		x : display in hex
 		w : word (its a size letter)

![view_stack](./img/gdb/view_stack.png)
