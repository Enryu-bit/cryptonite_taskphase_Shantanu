# Shell Variables
## Printing Variables
Learnt about the `echo` command which is used to print out stuff on screen.<br>
It can also print variables by using `$` before their name.<br>
In this challenge the flag was in the variable named `FLAG` and I had to print it out using `echo` command.<br>
```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{cbHm-VwdsuS4mYzQeUwaMFd2_RI.ddTN1QDLzYTN0czW}
```
## Setting Variables
Learnt how to assign values to variables in shell.<br>
`var=1337` note: there should not be a gap after or before `=` or else the shell will treat each segment as a different command.<br>
I also had a doubt regarding the assignment of string values.<br>
The doubt was do i assign the value with a `""` or just normally.<br>
Then I used GFG to address this one.<br>
Reference
`https://www.geeksforgeeks.org/string-manipulation-in-shell-scripting/`.<br>
```bash
hacker@variables~setting-variables:~$ PWN="COLLEGE"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IBFICF6bM_h0a9KPqypgL5k-5GK.dlTN1QDLzYTN0czW}
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IBFICF6bM_h0a9KPqypgL5k-5GK.dlTN1QDLzYTN0czW}
```
## Multi-Word Variables
Learnt the usecase of `" "` and how it can be used to store multiple words inside a variable.<br>
This helps the shell recognize the string inside the `" "` as a single token rather than seperate commands.<br>
Then I used this as instructed by the challenge to get the flag.<br>
```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gQPipLURs32lINqvIF9Ij2KrtxD.dBjN1QDLzYTN0czW}
```
## Exporting Variables
Learnt about scope of variables in shell.<br>
Learnt how by default when variables are created, they are not inherited by the child of the main shell.<br>
we have to use the `export command` to export them to the child shell.<br>
```bash
This concept was fairly simple to understand for me as similar things are there in Java called `Scope of Variables` and thus I had no problem obtaining the flag.<br>
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{AwlTjoQaRdlZZpfWTuQ2oGAbb8p.dJjN1QDLzYTN0czW}
```
