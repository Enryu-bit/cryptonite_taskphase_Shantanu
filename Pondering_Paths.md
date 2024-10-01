# Pondering Paths
## The root
learnt about the tree filesystem in linux. <br>
learnt about what a root(directory) is and how it can contain multiple directories inside it. <br>
the address of the directory is path. <br>
By looking at the path we could trace back to the root. <br>
invoked `/pwn` program to get the flag. <br>
command - `/pwn` <br>
```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{03UUW0oZ7Ug9wvECUpmfIrD20rS.dhzN5QDLzYTN0czW}
```
## Program And Absolute Paths
earlier I learnt theory about what directories are, in this challenge I had to access a program by using its path to get the flag <br>
command- `/challenge/run`
```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{wscSDBufS1YxbjtwmgQctAoftup.dVDN1QDLzYTN0czW}
```
## Position Thy Self
This was interesting...at first I `cd` into a directory called challenge. <br>
there was another directory called `run` there so i went in there. <br>
when i tried to run the program by `/challenge/run` it showed me incorect. <br>
It prompted me that i was not in the home directory so I `cd` to home and run the same `/challenge/run` and i get the flag.
command - <br> 
`cd /challenge` <br>
`cd /run`<br>
`cd /home`<br>
`/challenge/run`
```bash
hacker@paths~position-thy-self:~$ cd /challenge
hacker@paths~position-thy-self:/challenge$ cd /run
hacker@paths~position-thy-self:/run$ /challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/run$ cd /home
hacker@paths~position-thy-self:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Ah3qfsVm5xT_HJU4F_be1q3ndtt.dZDN1QDLzYTN0czW}
```
## Position Elsewhere
In this i tried running `/challenge/run`<br>
It prompted me to go to `/var/lib/apt/lists` and run there. <br>
I used cd to go to that directory using `cd /var/lib/apt/lists`<br>
Used the `/challenge/run` to get the flag.<br>
```bash
hacker@paths~position-elsewhere:/run$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:/var/lib/apt$ cd /var/lib/apt/lists
hacker@paths~position-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4UnyJHKRbj7yPvb8Vn7C9M3Ra9M.ddDN1QDLzYTN0czW}
```
## Position Yet Elsewhere
This was rather simple than the previous one. <br>
just had to `/challenge/run` and it prompted me to go to `/var` directory. <br>
Used `cd /var` to go there and executed `/challenge/run` to get the flag. <br>
```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var
hacker@paths~position-yet-elsewhere:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QIFo3tKKHujDZQAfqgTroNiEnKN.dhDN1QDLzYTN0czW}
```
## Implicit Relative Paths, from / .
In this challenge I learnt the difference between relative path and absolute path. <br>
Absolute paths will always contain `/` in start.<br>
I used `cd` to go to root folder. `cd /`. <br>
then used `challenge/run` to get the flag. <br>
```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{s-ZO8EEgriXLhr_-UrQ96s9ggwc.dlDN1QDLzYTN0czW}
```
