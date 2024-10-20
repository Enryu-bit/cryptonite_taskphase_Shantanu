e# Level 0
Connected to ssh of bandit0 and then read a readme file to obtain the pass for Level 1.<br>
```bash
shantanu@Shantanus-MacBook-Pro ~ % ssh -p 2220 bandit0@bandit.labs.overthewire.org
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password:

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
# Level 1
Learnt that files that begin with `-` or special can be read by `./-` by using `./-`.<br>
```bash
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
# Level 2
Learnt 2 ways to read files that have spaces in their file name to obtain the pass for next level.<br>
It can be either`a/ b/ c` or `"a b c"`.<br>
```bash
bandit2@bandit:~$
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat spaces\ in\ this\ filename
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
# Level 3
There was a hidden file in a directory which had the pass to the next level.<br>
Did `ls -a` to see it then used `cat`.<br>
```bash
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ ls inhere/
bandit3@bandit:~$ ls -a inhere/
.  ..  ...Hiding-From-You
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
# Level 4
There were many files in a directory but i didn't know how to find which file had the human readable content so after some research i found out by the combination of `find` and `file` commands we could do it.<br>
`find . -type f -exec file {} +`<br>
This command means that first we will find the files in `.` which is the cwd.<br>
then we specify that we are looking for files by `-type f`.<br>
then the `-exec` means that we want to perform some actions on then like gaining their file type by `file {} +` at once.<br>
```bash
bandit4@bandit:~/inhere$ find . -type f -exec file {} +
./-file08: data
./-file02: data
./-file09: data
./-file01: data
./-file00: data
./-file05: data
./-file07: ASCII text
./-file03: data
./-file06: data
./-file04: data
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
# Level 5
Very intersting level. had to find a file which had certain conditions and a size of 1033 bytes.<br>
So as i used the find command previously then added another exec function to do ls -l {} + and piped the output of this in grep command which was finding 1033(bytes).<br>
```bash
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ find . -type f -!executable
-bash: !executable: event not found
bandit5@bandit:~/inhere$ find . -type f ! -executable -exec file {} +
./maybehere02/-file2:       X1 archive data
./maybehere02/.file2:       ASCII text, with very long lines (2576)
./maybehere02/spaces file2: ASCII text, with very long lines (8487)
./maybehere19/-file2:       ASCII text, with very long lines (5593)
./maybehere19/.file2:       ASCII text, with very long lines (4739)
./maybehere19/spaces file2: ASCII text, with very long lines (8784)
./maybehere08/-file2:       ASCII text, with very long lines (3824)
./maybehere08/.file2:       ASCII text, with very long lines (746)
./maybehere08/spaces file2: ASCII text, with very long lines (3692)
./maybehere15/-file2:       ASCII text, with very long lines (9498)
./maybehere15/.file2:       ASCII text
./maybehere15/spaces file2: ASCII text
./maybehere03/-file2:       ASCII text, with very long lines (6594)
./maybehere03/.file2:       ASCII text, with very long lines (8879)
./maybehere03/spaces file2: ASCII text, with very long lines (3384)
./maybehere01/-file2:       ASCII text
./maybehere01/.file2:       ASCII text, with very long lines (3069)
./maybehere01/spaces file2: ASCII text, with very long lines (4542)
./maybehere00/-file2:       ASCII text, with very long lines (9387)
./maybehere00/.file2:       ASCII text, with very long lines (7835)
./maybehere00/spaces file2: ASCII text, with very long lines (6849)
./maybehere12/-file2:       ASCII text
./maybehere12/.file2:       ASCII text, with very long lines (8243)
./maybehere12/spaces file2: ASCII text, with very long lines (2459)
./maybehere17/-file2:       ASCII text, with very long lines (1790)
./maybehere17/.file2:       ASCII text, with very long lines (8340)
./maybehere17/spaces file2: ASCII text, with very long lines (3386)
./maybehere05/-file2:       ASCII text, with very long lines (5958)
./maybehere05/.file2:       ASCII text, with very long lines (5916)
./maybehere05/spaces file2: ASCII text, with very long lines (2419)
./maybehere09/-file2:       ASCII text, with very long lines (773)
./maybehere09/.file2:       ASCII text, with very long lines (8516)
./maybehere09/spaces file2: ASCII text, with very long lines (8715)
./maybehere06/-file2:       ASCII text, with very long lines (1075)
./maybehere06/.file2:       ASCII text, with very long lines (8975)
./maybehere06/spaces file2: ASCII text, with very long lines (4250)
./maybehere10/-file2:       ASCII text, with very long lines (1990)
./maybehere10/.file2:       ASCII text
./maybehere10/spaces file2: ASCII text, with very long lines (3569)
./maybehere11/-file2:       ASCII text, with very long lines (4558)
./maybehere11/.file2:       ASCII text, with very long lines (2500)
./maybehere11/spaces file2: ASCII text, with very long lines (502)
./maybehere07/-file2:       ASCII text, with very long lines (2487)
./maybehere07/.file2:       ASCII text, with very long lines (1000)
./maybehere07/spaces file2: ASCII text, with very long lines (9063)
./maybehere14/-file2:       ASCII text, with very long lines (8350)
./maybehere14/.file2:       ASCII text, with very long lines (1502)
./maybehere14/spaces file2: ASCII text, with very long lines (870)
./maybehere04/-file2:       ASCII text, with very long lines (2618)
./maybehere04/.file2:       ASCII text, with very long lines (6143)
./maybehere04/spaces file2: ASCII text, with very long lines (2490)
./maybehere13/-file2:       ASCII text, with very long lines (1422)
./maybehere13/.file2:       ASCII text, with very long lines (8951)
./maybehere13/spaces file2: ASCII text, with very long lines (951)
./maybehere18/-file2:       ASCII text
./maybehere18/.file2:       ASCII text, with very long lines (2083)
./maybehere18/spaces file2: ASCII text, with very long lines (6347)
./maybehere16/-file2:       ASCII text, with very long lines (5300)
./maybehere16/.file2:       ASCII text, with very long lines (8471)
./maybehere16/spaces file2: ASCII text, with very long lines (3145)
bandit5@bandit:~/inhere$ find . -type f ! -executable -exec file {} + -exec ls -l {} +
./maybehere02/-file2:       X1 archive data
./maybehere02/.file2:       ASCII text, with very long lines (2576)
./maybehere02/spaces file2: ASCII text, with very long lines (8487)
./maybehere19/-file2:       ASCII text, with very long lines (5593)
./maybehere19/.file2:       ASCII text, with very long lines (4739)
./maybehere19/spaces file2: ASCII text, with very long lines (8784)
./maybehere08/-file2:       ASCII text, with very long lines (3824)
./maybehere08/.file2:       ASCII text, with very long lines (746)
./maybehere08/spaces file2: ASCII text, with very long lines (3692)
./maybehere15/-file2:       ASCII text, with very long lines (9498)
./maybehere15/.file2:       ASCII text
./maybehere15/spaces file2: ASCII text
./maybehere03/-file2:       ASCII text, with very long lines (6594)
./maybehere03/.file2:       ASCII text, with very long lines (8879)
./maybehere03/spaces file2: ASCII text, with very long lines (3384)
./maybehere01/-file2:       ASCII text
./maybehere01/.file2:       ASCII text, with very long lines (3069)
./maybehere01/spaces file2: ASCII text, with very long lines (4542)
./maybehere00/-file2:       ASCII text, with very long lines (9387)
./maybehere00/.file2:       ASCII text, with very long lines (7835)
./maybehere00/spaces file2: ASCII text, with very long lines (6849)
./maybehere12/-file2:       ASCII text
./maybehere12/.file2:       ASCII text, with very long lines (8243)
./maybehere12/spaces file2: ASCII text, with very long lines (2459)
./maybehere17/-file2:       ASCII text, with very long lines (1790)
./maybehere17/.file2:       ASCII text, with very long lines (8340)
./maybehere17/spaces file2: ASCII text, with very long lines (3386)
./maybehere05/-file2:       ASCII text, with very long lines (5958)
./maybehere05/.file2:       ASCII text, with very long lines (5916)
./maybehere05/spaces file2: ASCII text, with very long lines (2419)
./maybehere09/-file2:       ASCII text, with very long lines (773)
./maybehere09/.file2:       ASCII text, with very long lines (8516)
./maybehere09/spaces file2: ASCII text, with very long lines (8715)
./maybehere06/-file2:       ASCII text, with very long lines (1075)
./maybehere06/.file2:       ASCII text, with very long lines (8975)
./maybehere06/spaces file2: ASCII text, with very long lines (4250)
./maybehere10/-file2:       ASCII text, with very long lines (1990)
./maybehere10/.file2:       ASCII text
./maybehere10/spaces file2: ASCII text, with very long lines (3569)
./maybehere11/-file2:       ASCII text, with very long lines (4558)
./maybehere11/.file2:       ASCII text, with very long lines (2500)
./maybehere11/spaces file2: ASCII text, with very long lines (502)
./maybehere07/-file2:       ASCII text, with very long lines (2487)
./maybehere07/.file2:       ASCII text, with very long lines (1000)
./maybehere07/spaces file2: ASCII text, with very long lines (9063)
./maybehere14/-file2:       ASCII text, with very long lines (8350)
./maybehere14/.file2:       ASCII text, with very long lines (1502)
./maybehere14/spaces file2: ASCII text, with very long lines (870)
./maybehere04/-file2:       ASCII text, with very long lines (2618)
./maybehere04/.file2:       ASCII text, with very long lines (6143)
./maybehere04/spaces file2: ASCII text, with very long lines (2490)
./maybehere13/-file2:       ASCII text, with very long lines (1422)
./maybehere13/.file2:       ASCII text, with very long lines (8951)
./maybehere13/spaces file2: ASCII text, with very long lines (951)
./maybehere18/-file2:       ASCII text
./maybehere18/.file2:       ASCII text, with very long lines (2083)
./maybehere18/spaces file2: ASCII text, with very long lines (6347)
./maybehere16/-file2:       ASCII text, with very long lines (5300)
./maybehere16/.file2:       ASCII text, with very long lines (8471)
./maybehere16/spaces file2: ASCII text, with very long lines (3145)
-rw-r----- 1 root bandit5 9388 Sep 19 07:08 ./maybehere00/-file2
-rw-r----- 1 root bandit5 7836 Sep 19 07:08 ./maybehere00/.file2
-rw-r----- 1 root bandit5 6850 Sep 19 07:08 ./maybehere00/spaces file2
-rw-r----- 1 root bandit5  288 Sep 19 07:08 ./maybehere01/-file2
-rw-r----- 1 root bandit5 3070 Sep 19 07:08 ./maybehere01/.file2
-rw-r----- 1 root bandit5 4543 Sep 19 07:08 ./maybehere01/spaces file2
-rw-r----- 1 root bandit5 3511 Sep 19 07:08 ./maybehere02/-file2
-rw-r----- 1 root bandit5 2577 Sep 19 07:08 ./maybehere02/.file2
-rw-r----- 1 root bandit5 8488 Sep 19 07:08 ./maybehere02/spaces file2
-rw-r----- 1 root bandit5 6595 Sep 19 07:08 ./maybehere03/-file2
-rw-r----- 1 root bandit5 8880 Sep 19 07:08 ./maybehere03/.file2
-rw-r----- 1 root bandit5 3385 Sep 19 07:08 ./maybehere03/spaces file2
-rw-r----- 1 root bandit5 2619 Sep 19 07:08 ./maybehere04/-file2
-rw-r----- 1 root bandit5 6144 Sep 19 07:08 ./maybehere04/.file2
-rw-r----- 1 root bandit5 2491 Sep 19 07:08 ./maybehere04/spaces file2
-rw-r----- 1 root bandit5 5959 Sep 19 07:08 ./maybehere05/-file2
-rw-r----- 1 root bandit5 5917 Sep 19 07:08 ./maybehere05/.file2
-rw-r----- 1 root bandit5 2420 Sep 19 07:08 ./maybehere05/spaces file2
-rw-r----- 1 root bandit5 1076 Sep 19 07:08 ./maybehere06/-file2
-rw-r----- 1 root bandit5 8976 Sep 19 07:08 ./maybehere06/.file2
-rw-r----- 1 root bandit5 4251 Sep 19 07:08 ./maybehere06/spaces file2
-rw-r----- 1 root bandit5 2488 Sep 19 07:08 ./maybehere07/-file2
-rw-r----- 1 root bandit5 1033 Sep 19 07:08 ./maybehere07/.file2
-rw-r----- 1 root bandit5 9064 Sep 19 07:08 ./maybehere07/spaces file2
-rw-r----- 1 root bandit5 3825 Sep 19 07:08 ./maybehere08/-file2
-rw-r----- 1 root bandit5  747 Sep 19 07:08 ./maybehere08/.file2
-rw-r----- 1 root bandit5 3693 Sep 19 07:08 ./maybehere08/spaces file2
-rw-r----- 1 root bandit5  774 Sep 19 07:08 ./maybehere09/-file2
-rw-r----- 1 root bandit5 8517 Sep 19 07:08 ./maybehere09/.file2
-rw-r----- 1 root bandit5 8716 Sep 19 07:08 ./maybehere09/spaces file2
-rw-r----- 1 root bandit5 1991 Sep 19 07:08 ./maybehere10/-file2
-rw-r----- 1 root bandit5   99 Sep 19 07:08 ./maybehere10/.file2
-rw-r----- 1 root bandit5 3570 Sep 19 07:08 ./maybehere10/spaces file2
-rw-r----- 1 root bandit5 4559 Sep 19 07:08 ./maybehere11/-file2
-rw-r----- 1 root bandit5 2501 Sep 19 07:08 ./maybehere11/.file2
-rw-r----- 1 root bandit5  503 Sep 19 07:08 ./maybehere11/spaces file2
-rw-r----- 1 root bandit5  251 Sep 19 07:08 ./maybehere12/-file2
-rw-r----- 1 root bandit5 8244 Sep 19 07:08 ./maybehere12/.file2
-rw-r----- 1 root bandit5 2460 Sep 19 07:08 ./maybehere12/spaces file2
-rw-r----- 1 root bandit5 1423 Sep 19 07:08 ./maybehere13/-file2
-rw-r----- 1 root bandit5 8952 Sep 19 07:08 ./maybehere13/.file2
-rw-r----- 1 root bandit5  952 Sep 19 07:08 ./maybehere13/spaces file2
-rw-r----- 1 root bandit5 8351 Sep 19 07:08 ./maybehere14/-file2
-rw-r----- 1 root bandit5 1503 Sep 19 07:08 ./maybehere14/.file2
-rw-r----- 1 root bandit5  871 Sep 19 07:08 ./maybehere14/spaces file2
-rw-r----- 1 root bandit5 9499 Sep 19 07:08 ./maybehere15/-file2
-rw-r----- 1 root bandit5  279 Sep 19 07:08 ./maybehere15/.file2
-rw-r----- 1 root bandit5   51 Sep 19 07:08 ./maybehere15/spaces file2
-rw-r----- 1 root bandit5 5301 Sep 19 07:08 ./maybehere16/-file2
-rw-r----- 1 root bandit5 8472 Sep 19 07:08 ./maybehere16/.file2
-rw-r----- 1 root bandit5 3146 Sep 19 07:08 ./maybehere16/spaces file2
-rw-r----- 1 root bandit5 1791 Sep 19 07:08 ./maybehere17/-file2
-rw-r----- 1 root bandit5 8341 Sep 19 07:08 ./maybehere17/.file2
-rw-r----- 1 root bandit5 3387 Sep 19 07:08 ./maybehere17/spaces file2
-rw-r----- 1 root bandit5   77 Sep 19 07:08 ./maybehere18/-file2
-rw-r----- 1 root bandit5 2084 Sep 19 07:08 ./maybehere18/.file2
-rw-r----- 1 root bandit5 6348 Sep 19 07:08 ./maybehere18/spaces file2
-rw-r----- 1 root bandit5 5594 Sep 19 07:08 ./maybehere19/-file2
-rw-r----- 1 root bandit5 4740 Sep 19 07:08 ./maybehere19/.file2
-rw-r----- 1 root bandit5 8785 Sep 19 07:08 ./maybehere19/spaces file2
bandit5@bandit:~/inhere$ find . -type f ! -executable -exec file {} + -exec ls -l {} + | grep 1033
-rw-r----- 1 root bandit5 1033 Sep 19 07:08 ./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
