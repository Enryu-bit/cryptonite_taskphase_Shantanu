# Processes and Jobs
## Listing Processes
Learnt the use of `ps` which can be used to see the current running processes in pc.<br>
Learnt about various arguments and how they differ by style --standard , --BSD.<br>
In `Standard` the syntax is you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.<br>
In `BSD` you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.<br>
They seem similar but are slightly different.<br>
To obtain flag I had to find a file that was in the challenge directory that was running.<br>
After finding it i had to rerun it.<br>
```bash
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  1.5  0.0   1056   640 ?        Ss   20:56   0:00 /sbin/docker-init -- /nix/var/nix/profiles/defa
root           7  0.2  0.0   5052  2560 ?        S    20:56   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    20:56   0:00 /challenge/19084-run-14142
root          72  0.0  0.0   2744  1600 ?        S    20:56   0:00 sleep 6h
hacker        73  2.0  0.0   5372  3840 pts/1    Ss+  20:56   0:00 /run/dojo/bin/ssh-entrypoint
hacker        79  2.5  0.0   5372  3840 pts/0    Ss   20:56   0:00 /run/dojo/bin/ssh-entrypoint
hacker       107  0.0  0.0   7868  3200 pts/0    R+   20:56   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/19084-run-14142
Yahaha, you found me! Here is your flag:
pwn.college{QIQbDotNlB9LqckpveclWRXioeU.dhzM4QDLzYTN0czW}
```
## Killing Processes
Learnt about the `kill` command which is used to kill a running process by giving its `PID` number as an argument to it.<br>
To get flag in this challenge i had to kill the `/challenge/dont_run` process and then run the `/challenge/run`.<br>
So to first find the process i took inspiration from the example and used a bit of piping to find the running process.<br>
Used `ps aux | grep challenge` and then used kill with PID to eliminate.<br>
```bash
hacker@processes~killing-processes:~$ ps aux | grep challenge
root          71  0.0  0.0   4732  3200 ?        S    21:03   0:00 su -c /challenge/.launcher hacker
hacker        73  0.0  0.0   4976  3200 ?        Ss   21:03   0:00 /challenge/dont_run
hacker        93  0.0  0.0   4140  2240 pts/0    S+   21:03   0:00 grep --color=auto challenge
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{Eht8MqAVCzFopTV1W6nRfGH-5fe.dJDN4QDLzYTN0czW}
```
##
