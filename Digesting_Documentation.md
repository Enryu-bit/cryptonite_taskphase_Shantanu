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
## Searching Manuals
Read the man page for challenge.<br>
Passed the correct argument to get the flag.<br>
```bash
man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --by
Initializing...
Correct usage! Your flag: pwn.college{8czav-iFmpUMMFwDCjaa9a21-ov.dVTM4QDLzYTN0czW}
```
## Searching For Manuals
In this I learnt commands like `man -f filename` and other man command specific arguments which helped me get to the man page of `/challenge/challenge`.<br>
This page had clues to what to give as arguments to obtain the flag.<br>
```bash
hacker@man~searching-for-manuals:/challenge$ man -f /challenge/challenge
krcijnyfbq (1)       - print the flag!
hacker@man~searching-for-manuals:/challenge$ man krcijnyfbq

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

       --krcijn NUM
              print the flag if NUM is 735

AUTHOR
       Written by Zardus.

hacker@man~searching-for-manuals:/challenge$ /challenge/challenge        --krcijn NUM
Incorrect usage! Please read the challenge man page!
hacker@man~searching-for-manuals:/challenge$ /challenge/challenge        --krcijn 735
Correct usage! Your flag: pwn.college{kr7YcijnUSyVf3KP58bq9FsvmX9.dZTM4QDLzYTN0czW}
```
## Helpful Programs
Learnt about the `--help` argument that helps us navigate.<br>
Did what it told to get the flag.<br>
```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give
                        you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -g
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: expected one argument
hacker@man~helpful-programs:~$ /challenge/challenge -g -p
You passed -p as an argument to -g! Please read the usage
carefully: -g takes *its own* numerical argument.
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 654
hacker@man~helpful-programs:~$ /challenge/challenge -g 654
Correct usage! Your flag: pwn.college{gHd6k_u5VGV-SpHTH41cGHCPHaH.ddjM4QDLzYTN0czW}
```
