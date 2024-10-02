# Comprehending Commands
## Cat: Not The Pet, But The Command!
Learnt what the `cat` command does.<br>
It reads the content of the file given.<br>
If provided with multiple arguments it will read all of them. <br>
Both Absolute and Relative paths can be passed as arguments.<br>
Used `cat flag` to get the flag.<br>
```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{AeVcBqpXa9hHi7xRNzJXqviQ6d5.dFzN1QDLzYTN0czW}
```
## Catting Absolute Paths
As mentioned above absolute paths can be passed as arguments to `cat` command.<br>
so it was given in the challenge that flag was not directly in home so used `cat /flag` to get it.<br>
```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{AvQKF8iHma2EB9MVFUadqKOZI2b.dlTM5QDLzYTN0czW}
```
## More Catting Practice
In this challenge I wasn't allowed to use cd to get to flag directly.<br>
Rather than that I had to use the whole absolute path as an argument to the cat command.<br>
As I was lost and didn't know where flag was so i used cd(which was prohibited).<br>
The terminal then gave me the exact path so i used the `cat` command to access it.<br>
command - `cat /opt/radare2/sys/flag` to get the flag.<br>
```bash
hacker@commands~more-catting-practice:~$ cat /opt/radare2/sys/flag
pwn.college{wq6D2GrJM13Z52vcHyGuZkqx4YL.dBjM5QDLzYTN0czW}
```
## Grepping For A Needle In A Haystack
Learnt to use the `grep` command and how It can be used to traverse the whole content of a file and provide us with a line that has that string. <br>
`grep a b` has two arguments where a = string to be searched and b = the absolute path of that file.txt in which it is to be searched.<br>
```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{UBTYryae5dxPMecOJUIxzLWTwcm.ddTM4QDLzYTN0czW}
```
## Listing Files
Learnt about the `ls` command and how it can be used to know the contents of a directory.<br>
In this challenge the file run was renamed so i used `ls /challenge` to know the name of the renamed file.<br>
Then used `/challenge/renamed` to run it to get the flag.<br>
```bash
hacker@commands~listing-files:~$ ls /challenge
32613-renamed-run-28805  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/32613-renamed-run-28805
Yahaha, you found me! Here is your flag:
pwn.college{c859Ym-hvggMM4HAd8gfcciCQ9b.dhjM4QDLzYTN0czW}
```
## Touching Files
This was fairly simple. I had to create two files in the `tmp` directory by using the `touch` command.<br>
After that used `/challenge/run` to get the flag.<br>
```bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{UQ_S2lVvuqpumAebylYJpm4kfLb.dBzM4QDLzYTN0czW}
```
## Removing Files
In this I learnt about rm command and how it is used to delete files from a directory.<br>
After I Deleted the file using `rm delete_me` then used `/challenege/check` to get the flag.<br>
```bash
hacker@commands~removing-files:~$ ls
delete_me  h
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{AnDWP57Iysy1LnxTgCZ4Ew77Kav.dZTOwUDLzYTN0czW}
```

