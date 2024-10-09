# Practicing Piping
## Redirecting Output
`>` this is used to redirect content to one file and which can be accessed by `cat file`.<br
To get the flag i had to redirect `PWN` to a file named `COLLEGE`.<br>
```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{QeaoWUDTaoNsJkQ8u1iaU9KeUm_.dRjN1QDLzYTN0czW}
```
## Redirecting More Output
In this I had to redirect `/challenge/run` to a file named `myflag`.<br>
It Still printed to my terminal but when i did `cat myflag` it gave me the flag.<br>
```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{04mPZUBb8PLX2QLe4dnNrrY7orB.dVjN1QDLzYTN0czW}
```
## Appending Output
Learnt About the `>>` operator that will not overwrite but append the content to the current file.<br>
so I first used `>>` on `/challenge/run` to append.<br>
Then used cat to read the flag.<br>
```bash
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{Iin6i3tKRWyyqIyfEWRLfFYNkkJ.ddDM5QDLzYTN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```
## Redirecting Errors
Learnt about file descriptor numbers(FD) where default is 1.<br>
FD 0: Standard Input.<br>
FD 1: Standard Output.<br>
FD 2: Standard Error.<br>
In this challenge we had to put the output in a file called `myflag` and the errors in `instructions`.<br>
```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{IXwuvb9QbLfE27KcUz0pyBgv76B.ddjN1QDLzYTN0czW}
```
## Redirecting Input
Learnt about `<` operator that is used to redirect input to a file.<br>
First used echo to input `COLLEGE`  in `PWN` .<br>
And then used the `<` to redirect the input to `/challenge/run < PWN` to get the flag.<br>
```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{cY68rJXP6X05DvYZD5Fbr4cT7sb.dBzN1QDLzYTN0czW}
```
## Grepping Stored Results
In this challenge we had to use our prior knowledge of grep command to grep the flag.<br>
After Storing the output of `/challenge/run` to a file, I used `grep pwn /path of file` to get the flag.<br>
```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn /tmp/data.txt
pwn
pwn.college{Yz-iKoMJGhTeFc8J18xWm1KRhXr.dhTM4QDLzYTN0czW}
pwned
pwning
pwns
```
## Grepping Live Output
Learnt about the piping operator `|`.<br>
This connects the std output of the command on left to the std input to the right.<br>
I then used `/challenge/run | grep pwn` to get the flag.<br>
```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{0vftd-RZOw9EhkgSVWMG37HUq2U.dlTM4QDLzYTN0czW}
pwn
pwned
pwning
pwns
```
## Grepping Errors
we know that `|` operator only links output to input but not errors.<br>
So we use `>&` to change the format of errors to output and then pipe it with grep to get the flag.<br>
```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1  /file | grep pwn /file
grep: /file: No such file or directory
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   Unable to find the process on the other end of the stderr pipe. There are many possible reasons for this, with the following three being the most likely:
	(1) The process on the other end of the pipe was launched with invalid arguments and quickly errored out, so it was gone by the time we checked. If that's the case, figure out the right arguments!
	(2) The process on the other end of the pipe was a fast-running processs (such as `cat some_file`, which just yeets the file to its stdout and exits). If that's the case, figure out how to make the process stick around!
	(3) This check happened *before* the other process successfully launched. This is a common occurrence if you're trying to redirect the stdout of this challenge to another process, you're manually doing this in an interactive ipython, and you're launching the challenge before launching the other process. Try pasting in both pwntools or subprocess invocations rapidly one after the other to get the second process launched in time!
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1  /file | grep pwn
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn
pwns
pwn.college{oFlX_Kyy1UqGQ7LSwkXhCDi-5mg.dVDM5QDLzYTN0czW}
pwned
```
## Duplicating Piped Data With Tee
Learnt about `tee` command and how it is used to intercept data between piping.<br>
Used `tee` command to overwrite pwn file with the secret argument.<br>
Then used `cat pwn` to read the secret argument and passed it to get flag.<br>
```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwn | /challenge/college
Processing...
WARNING: you are overwriting file pwn with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "0qBYKEJK"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret 0qBYKEJK | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{0qBYKEJKfODxmG1LeswmgkQOTfm.dFjM5QDLzYTN0czW}
```
## Writing To Multiple Programs
I piped the output of `/challenge/hack` to `/challenge/the` and `/challenge/planet`.<br>
And got the flag.<br>
```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
24698319929301915
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{EXSD6CBS1aWv4DhSyY58D4YauTk.dBDO0UDLzYTN0czW}
```
## Split-Piping Stderr and Stdout
Used 2> >() to redirect error and and > >() to redirect output.<br>
From previous challenges and info in this, this was pretty straight forward.<br>
```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{AvmDB4_ae1EmrB1dTRweQfi4NTT.dFDNwYDLzYTN0czW}
```
