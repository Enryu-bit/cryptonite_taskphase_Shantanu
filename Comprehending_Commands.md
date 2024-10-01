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
