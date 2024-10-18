# Untangling Users
## Becoming Root with the su
Learnt that we can use the `su` command to become root by inputting the correct password.<br>
In this challenge to get the flag i used the `su` command to become the root and then read the flag file.<br>
```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{wGEqk_fEdJKLEhsO3FQ6tgXHUp4.dVTN0UDLzYTN0czW}
```
## Other users with su
We can become other users if the arg to su command is the name of some user we want to access.<br>
In this challenge switch to zardus user and then run `/challenge/run` to get the flag.<br>
```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{o2WPCFCvrzKsB_RgrLeRJlXvCL9.dZTN0UDLzYTN0czW}
```
## Cracking Passwords
learnt that sometime the backup file of the `/etc/shadow` can be leaked by backup files and then we can use tools like `John The Ripper` to decode the encrypted password obtained by the leak.<br>
In this challenge a leaked backup file was provided to me and then i used john the ripper tool to decrypt the encrypted password.<br>
Then used the su command to gain access to zardus user and then got the flag.<br>
```bash
hacker@users~cracking-passwords:~$ john ./challenge/shadow-leak
Created directory: /home/hacker/.john
stat: ./challenge/shadow-leak: No such file or directory
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:06 76% 1/3 0g/s 323.5p/s 323.5c/s 323.5C/s 9999945..Z9999932
aardvark         (zardus)
1g 0:00:00:17 100% 2/3 0.05672g/s 330.2p/s 330.2c/s 330.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{Mtmai2zdreeJFuJjte658WoLdMz.ddTN0UDLzYTN0czW}
```
## Using Sudo
Learnt about the `sudo` command and how it evolved from `su`.<br>
This command rather than giving access to the whole root shell runs specific commands by root access if it preceeds them.<br>
Used it to read the flag.<br>
```bash
hacker@users~using-sudo:~$ ls
COLLEGE  cmd      h             myflag        pwn
PWN      college  instructions  not-the-flag  the-flag
hacker@users~using-sudo:~$ cat not-the-flag
cat: not-the-flag: Permission denied
hacker@users~using-sudo:~$ sudo cat not-the-flag
pwn.college{IRNMylywJ9C6jR7uQFniuIN9PT1.dhTN0UDLzYTN0czW}
```
