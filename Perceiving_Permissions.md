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
