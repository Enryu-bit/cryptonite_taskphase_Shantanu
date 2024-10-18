# Chaining Commands
## Chaining with Semicolons
Learnt the use of `;` and how it can be used to run multiple commands in a single line.<br>
It has the same use as when we press enter to run a command and then it terminates.<br>
```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{oJIyOCw36RCTnw4YnteB0apFnmP.dVTN4QDLzYTN0czW}
```
## Your First Shell Script
In this i was confused how to make a shell script then i referred to a link `https://www.geeksforgeeks.org/how-to-create-a-shell-script-in-linux/` to learn how to make a script using the nano command.<br>
So i did it and got the flag.<br>
I didn't update the permission becaused i didn't had to execute that file.<br>
```bash
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{szsDHE7j3oUIOPZk1XCUBuYunKB.dFzN4QDLzYTN0czW}
```
## Redirecting Script Output
Learnt that the whole script execution acts as a single command then we can redirect its output, error, input like we learned previously.<br>
So as the challenge instructed i redirected the output of a script to the input of a file.<br>
```bash
hacker@chaining~redirecting-script-output:~$ touch script.sh
hacker@chaining~redirecting-script-output:~$ nano script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{YxHm1RWE0tw7wp9ZwoNCHZRX-9i.dhTM5QDLzYTN0czW}
```
## Executable Shell Scripts
Learnt that we can skip the `bash` command and rather just execute the script like `./script.sh` and get the output.<br>
We also need to give it permissions via `chmod` command.<br>
```bash
hacker@chaining~executable-shell-scripts:~$ touch x.sh
hacker@chaining~executable-shell-scripts:~$ nano x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u=x x.sh
hacker@chaining~executable-shell-scripts:~$ ls -l
total 44
---------- 1 hacker hacker   4 Oct  8 17:41 COLLEGE
---------- 1 hacker hacker   8 Oct  9 07:28 PWN
---------- 1 root   hacker  77 Oct  9 14:12 cmd
---------- 1 hacker hacker   4 Oct  9 07:27 college
---------- 1 hacker hacker  58 Oct  1 16:33 h
---------- 1 hacker hacker 829 Oct  8 19:07 instructions
---------- 1 hacker hacker  93 Oct  8 19:07 myflag
lrwxrwxrwx 1 hacker hacker   5 Oct  3 16:09 not-the-flag -> /flag
---------- 1 hacker hacker  77 Oct  9 14:14 pwn
-rw-r--r-- 1 hacker hacker  35 Oct 18 11:00 script.sh
---------- 1 hacker hacker 435 Oct  8 18:59 the-flag
---xr--r-- 1 hacker hacker  17 Oct 18 11:05 x.sh
hacker@chaining~executable-shell-scripts:~$ chmod ugo+rwx  x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{s-k2FdyulL-W5s0KyK2lT5ud7xw.dRzNyUDLzYTN0czW}
```
