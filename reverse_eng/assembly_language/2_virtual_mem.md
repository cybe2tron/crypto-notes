# virtual memory organization

 to see memory laid out of a proram in memory.

 1. find out process id

 ```
 ps -aux | grep <program_name>
 ```
 2. /proc dir hold runtime info about processes which happenig in kernel.

 in `/proc/pid/maps` file contain memory layout.