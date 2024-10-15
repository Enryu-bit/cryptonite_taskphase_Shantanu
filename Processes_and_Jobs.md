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
## Interrupting Processes
Sometimes we want to terminate the currently running process so to do that we can use the `Ctrl + c` to terminate it quickly.<br>
In this i had to first run `/challenge/run` and then use `Ctrl + c` to get the flag.<br>
```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{MOH8o-Kk90wnbp_90lyYyGlq0oi.dNDN4QDLzYTN0czW}
```
## Suspending Processes
We can use ` Ctrl + z` to suspend processes to the background and then can run multiple instances of it.<br>
In this to obtain the flag i had to run 2 instances of `/challenge/run` by suspending the first one and then run it again.<br>
```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 21:11 pts/0    00:00:00 bash /challenge/run
root          84      82  0 21:11 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 21:11 pts/0    00:00:00 bash /challenge/run
root          89      65  0 21:11 pts/0    00:00:00 bash /challenge/run
root          91      89  0 21:11 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{MGsXZ7AT-k5DpEkRyplGAjtZixB.dVDN4QDLzYTN0czW}
```
## Resuming Processes
After suspending if we want the process to continue again then we can use the `fg` command.<br>
To get the flag i had to suspend the `/challenge/run` and then resume it by using `fg`.<br>
```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{QnTi_4DJHwUPkU8O5JcncaG_q1_.dZDN4QDLzYTN0czW}
```
## Backgrounding Process
Learnt that we can resume the process in the background by using the `bg` command.<br>
By doing this we can do some other tasks while it is being activated in the background.<br>
To get the flag we had to have 2 instances of `/challenge/run` running simultaneously.<br>
so first i used run then suspended it then resumed it with `bg` then used another run to get the flag.<br>
```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          83 S+   bash /challenge/run
root          85 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          83 S    bash /challenge/run
root          93 S    sleep 6h
root          94 S+   bash /challenge/run
root          96 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{YjB6NciQA_a0g74-tIXav7VvqYT.ddDN4QDLzYTN0czW}
```
## Foregrounding Process
Learnt that we can foreground a background process as well by using the fg command.<br>
so first i suspended a process then used `bg` to resume it in background.<br>
then used fg to foreground the resumed background process.<br>
```bash
hacker@processes~foregrounding-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.0   1056   640 ?        Ss   08:42   0:00 /sbin/docker-
root           7  0.0  0.0   5052  2560 ?        S    08:42   0:00 /run/dojo/bin
hacker        65  0.4  0.0   5372  3840 pts/0    Ss   08:43   0:00 /run/dojo/bin
hacker        82  0.0  0.0   7868  3200 pts/0    R+   08:43   0:00 ps aux
hacker@processes~foregrounding-processes:~$ fg
ssh-entrypoint: fg: current: no such job
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{0VAPT88_VTreSxVuVBDUMqcFosM.dhDN4QDLzYTN0czW}
```
## Starting Background Processes
We dont always have to suspend the process to background it, we can start them in the background.<br>
To do this just append `&` at the end of the process to start it in background.<br>
```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{URkhU_2V91_nZHtOGEAAIEhFbnB.dlDN4QDLzYTN0czW}
```
## Process Exit codes
Learnt about what process exit codes are and how can i read the last exit code by reading the special variable `?` by using `echo $?`.<br>
To get the flag in this challenge i had to first run a process then get its exit code then pass that exit code to some other command to get the flag.<br>
```bash
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
147
hacker@processes~process-exit-codes:~$ /challenge/submit-code 147
CORRECT! Here is your flag:
pwn.college{4TEZ0hk-LZyKqn7T_mBZDR8B6TW.dljN4UDLzYTN0czW}
```
