# Pondering PATH
## The PATH Variable
Learnt that the `PATH` variable stores directories of programs that we use and dont need absolute or relative paths each time to make it run.<br>
If the PATH variable is cleared then we cant access these programs by say just writing `ls` or `rm`.<br>
In this challenge all i had to do is empty the `PATH` so that the program would not be able to access the `rm` command.<br>
```bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{E97DWZN6zcUW5CxkDS9jrWvdnPx.dZzNwUDLzYTN0czW}
```
## Setting PATH
We can set the PATH to a directory in which there is some program that we want to access just by its name.<br>
In this challenge i set the PATH to the `/challenge/more_commands to access the win inside it.<br>
```bash
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{cbaeZ0uoCQd-n1mvZT0P9_4PEJJ.dVzNyUDLzYTN0czW}
```
## Adding Commands
Learnt after long researching that we can add a new directory before the OG PATH by using the export command.<br>
Then I made the file named win with cat /flag.<br>
Then Appended the new PATH to the og one by `export PATH=/home/hacker:$PATH`.<br>
```bash
PWN      college  instructions  not-the-flag  script.sh  x.sh
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~adding-commands:~$ echo $PATH
/home/hacker:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: /home/hacker/win: Permission denied
It looks like that did not work... Did you set PATH correctly?
hacker@path~adding-commands:~$ chmod ugo+rwx /home/hacker/win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{osLhTScptnfviQ5elKFcrGFHFeH.dZzNyUDLzYTN0czW}
```
## Hijacking Commands
Tricky but like the first challenge it was trying to delete the /flag file but i made a new rm file in `/home/hacker`.<br>
this had `/bin/cat` to read out the flag and then removed the PATH and changed it to `/home/hacker`.<br>
```bash
hacker@path~hijacking-commands:~$ cat rm
cat /flag
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ export PATH=/home/hacker/
hacker@path~hijacking-commands:~$ echo $PATH
/home/hacker/
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{UiMsZje95HclQ2xNdDFO1ZkcR8v.ddzNyUDLzYTN0czW}
```
