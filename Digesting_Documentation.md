# Digesting Documentation
## Learning From Documentation
Learnt why documentation in programs is important.<br>
In this challenge learnt how to give arguments to get the desired results.<br>
used `/challenge/challenge --giveflag` to get the flag.<br>
```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{MHY5it0EZ5TOXOT_CwaFLsKI-rz.dRjM5QDLzYTN0czW}
```
## Learning Complex Usage
Learnt that arguments can be passed to arguments similar to the `find` command earlier.<br>
passed the location of `flag` file as an argument to the `--printfile` argument to get the flag.
```bash
hacker@man~learning-complex-usage:~$ cd /
hacker@man~learning-complex-usage:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@man~learning-complex-usage:/$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{As6MQaABX1QrvGDjFFdTqduIQ4H.dVjM5QDLzYTN0czW}
```
## Reading Manuals
Learnt about the `man` command and how it gives us the summary manual of a command.<br>
We dont enter the path, just the name of the command that we want the manual of.<br>
I used `man challenge` as per the challenge description.<br>
Then I had to used a command as per the requirements to obtain the flag.<br>
```bash
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                  Challenge Commands                  CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --pdhabo NUM
              print the flag if NUM is 840

AUTHOR
       Written by Zardus.

hacker@man~reading-manuals:~$ /challenge/challenge --pdhabo 840
Correct usage! Your flag: pwn.college{AYpdhHXRab8EVOobSujojkXXHRA.dRTM4QDLzYTN0czW}
```
