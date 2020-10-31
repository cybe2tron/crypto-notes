# Text Fu

> Mr.cyber7ron | Wed 21 Oct 2020


**stdout**

<span style="color: red;">```>```</span>  redirected output to file<br>
<span style="color: red;">```>>```</span>  redirect output to file without overwrite.<br>


**stdin**

<span style="color: red;">```<```</span>  for stdin redirection.<br>

**stderr**

*file descriptors* : <p>A file descriptor is a non-negative number that is used to access a file or stream.file descriptor for stdin, stdout and stderr is 0, 1, and 2 respectively.</p>

<span style="color: red;">```ls /fake/dir > file.txt 2>/dev/null```</span>  redirect error in /dev/null directory.<br>

<span style="color: red;">```ls /fake/dir > file.txt 2>&1```</span> redirected error where stdout pointed in this case file.txt<br>

* * * 

**pipe**

<span style="color: red;">```|```</span> get stdout of a cmd and make that stdin to another process.<br>

**tee**

<span style="color: red;">```ls | tee file.txt```</span>  show output on screen as well as save to file.txt<br>

**env**

it will show env variables and lots of other info.