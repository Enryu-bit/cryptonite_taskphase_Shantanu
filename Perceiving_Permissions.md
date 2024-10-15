# Perceiving Permissions
## Changing File Ownership
This module seems very interesting to me.<br>
Learn about permissions of file and how we can view them by using ls -l.<br>
learnt about that the first letter of the format means the type i.e. directory or file. Directory - `d` , file - `-`.<br>
Learnt about the 9 letters which tell us abou the permissions of user, group and other users.<br>
This challenge was fairly simple i had to change the permission of the `/flag` file to hacker user by using the `chown` command which can only be accessed by the root user but for this challenge i was able to use it to change the permission and then read the flag.<br>
```bash
hacker@permissions~changing-file-ownership:~$ ls -l
total 36
-rw-r--r-- 1 hacker hacker   4 Oct  8 17:41 COLLEGE
-rw-r--r-- 1 hacker hacker   8 Oct  9 07:28 PWN
-rw-r--r-- 1 root   hacker  77 Oct  9 14:12 cmd
-rw-r--r-- 1 hacker hacker   4 Oct  9 07:27 college
-rw-r--r-- 1 hacker hacker  58 Oct  1 16:33 h
-rw-r--r-- 1 hacker hacker 829 Oct  8 19:07 instructions
-rw-r--r-- 1 hacker hacker  93 Oct  8 19:07 myflag
lrwxrwxrwx 1 hacker hacker   5 Oct  3 16:09 not-the-flag -> /flag
-rw-r--r-- 1 hacker hacker  77 Oct  9 14:14 pwn
-rw-r--r-- 1 hacker hacker 435 Oct  8 18:59 the-flag
hacker@permissions~changing-file-ownership:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{su0y-3rI8k0tCz2bqZCavlmF_FU.dFTM2QDLzYTN0czW}
```
## Groups and Files
Learnt about how members of groups can access the files accessible to that group.<br>
used the chgrp command to change the group of the flag and then read it to obtain the flag.<br>
```bash
hacker@permissions~groups-and-files:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~groups-and-files:~$ ls -l
total 36
-rw-r--r-- 1 hacker hacker   4 Oct  8 17:41 COLLEGE
-rw-r--r-- 1 hacker hacker   8 Oct  9 07:28 PWN
-rw-r--r-- 1 root   hacker  77 Oct  9 14:12 cmd
-rw-r--r-- 1 hacker hacker   4 Oct  9 07:27 college
-rw-r--r-- 1 hacker hacker  58 Oct  1 16:33 h
-rw-r--r-- 1 hacker hacker 829 Oct  8 19:07 instructions
-rw-r--r-- 1 hacker hacker  93 Oct  8 19:07 myflag
lrwxrwxrwx 1 hacker hacker   5 Oct  3 16:09 not-the-flag -> /flag
-rw-r--r-- 1 hacker hacker  77 Oct  9 14:14 pwn
-rw-r--r-- 1 hacker hacker 435 Oct  8 18:59 the-flag
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{wUTbcNNGhbezEeRYTC4JCjpDoH3.dFzNyUDLzYTN0czW}
```
## Fun With Groups Names
This time my user group was named something different than hacker so i used the id command to get the group name and then used `chgrp` to change the permission of `/flag` to my new group name to read it.<br>
```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp32761) groups=1000(grp32761)
hacker@permissions~fun-with-groups-names:~$ ls -l
total 36
-rw-r--r-- 1 hacker grp32761   4 Oct  8 17:41 COLLEGE
-rw-r--r-- 1 hacker grp32761   8 Oct  9 07:28 PWN
-rw-r--r-- 1 root   grp32761  77 Oct  9 14:12 cmd
-rw-r--r-- 1 hacker grp32761   4 Oct  9 07:27 college
-rw-r--r-- 1 hacker grp32761  58 Oct  1 16:33 h
-rw-r--r-- 1 hacker grp32761 829 Oct  8 19:07 instructions
-rw-r--r-- 1 hacker grp32761  93 Oct  8 19:07 myflag
lrwxrwxrwx 1 hacker grp32761   5 Oct  3 16:09 not-the-flag -> /flag
-rw-r--r-- 1 hacker grp32761  77 Oct  9 14:14 pwn
-rw-r--r-- 1 hacker grp32761 435 Oct  8 18:59 the-flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~fun-with-groups-names:~$ chgrp grp32761 flag
chgrp: cannot access 'flag': No such file or directory
hacker@permissions~fun-with-groups-names:~$ chgrp grp32761 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{k275-xyYGyEafVwXbcC8M4midy6.dJzNyUDLzYTN0czW}
```
## Changing Permission
We can also change the access level of files by using the `chmod` command.<br>
to add we use `u` `g` `o` for user group and other user, to add read write execute, we can use ugo+-rwx and make all possible combinations you want.<br>
The format is `chmod permission file`.<br>
```bash
hacker@permissions~changing-permissions:~$ ls -l
total 36
---------- 1 hacker hacker   4 Oct  8 17:41 COLLEGE
---------- 1 hacker hacker   8 Oct  9 07:28 PWN
---------- 1 root   hacker  77 Oct  9 14:12 cmd
---------- 1 hacker hacker   4 Oct  9 07:27 college
---------- 1 hacker hacker  58 Oct  1 16:33 h
---------- 1 hacker hacker 829 Oct  8 19:07 instructions
---------- 1 hacker hacker  93 Oct  8 19:07 myflag
lrwxrwxrwx 1 hacker hacker   5 Oct  3 16:09 not-the-flag -> /flag
---------- 1 hacker hacker  77 Oct  9 14:14 pwn
---------- 1 hacker hacker 435 Oct  8 18:59 the-flag
hacker@permissions~changing-permissions:~$ chmod ugo+rwx /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{Y_32trqVVm9GXcGCCRDMO8PX9xI.dNzNyUDLzYTN0czW}
```
## Executable Files
Similar to the previous ones just now had to change the executing permission whereas before i was changing the read permisssion.<br>
```bash
hacker@permissions~executable-files:~$ ls -l /challenge/
total 32
-rwsr-xr-x 1 root   root    1222 Jul  4 06:38 DESCRIPTION.md
-rwsr-xr-x 1 root   root   16864 Feb  8  2024 getflag
-rwsr-xr-x 1 root   root     211 Feb  8  2024 getflag.c
-r--r--r-x 1 hacker hacker    32 Jul  4 06:37 run
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{4_rba5a5zNPF8jshRxEGxky9pTS.dJTM2QDLzYTN0czW}
```
## Permission Tweaking Practice
This challenge had nothing new but was a good practice of the chmod command.<br>
I had to change the file permission 8 times consecutively and at the end change tha flag to make it readable.<br>
```bash
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxr--r-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod uo+x  /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rwxr--r-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwx------
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod go-rx  /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": rwx------
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxr-----
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+r  /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": rwxr-----
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xr-----
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-w  /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": r-xr-----
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xrwx---
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+wx  /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": r-xrwx---
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--rw----
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ug-x  /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": r--rw----
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xrwxr-x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ugo+rx  /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": r-xrwxr-x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-xrwxrwx
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+w  /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ugo+rwx /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{0ymJeO284Gu-lkg9I3tHmMIKtn4.dBTM2QDLzYTN0czW}
```
## Permission setting Practice
