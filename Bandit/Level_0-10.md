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
# Level 6
Again by the use of `find` command, found files that met the conditions and then used cat to obtain the pass.<br>
Also learnt an amazing thing. as you can see there are many errors currently which make it hard to read where are file is so we can use `2> /dev/null` to delete all the errors.<br>
This directory `/dev/null` acts as a dustbin for us in linux.<br>
```bash
bandit6@bandit:/$ find . -size 33c -user bandit7 -group bandit6
find: ‘./drifter/drifter14_src/axTLS’: Permission denied
find: ‘./root’: Permission denied
find: ‘./snap’: Permission denied
find: ‘./tmp’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/3130225/task/3130225/fd/6’: No such file or directory
find: ‘./proc/3130225/task/3130225/fdinfo/6’: No such file or directory
find: ‘./proc/3130225/fd/5’: No such file or directory
find: ‘./proc/3130225/fdinfo/5’: No such file or directory
find: ‘./home/bandit31-git’: Permission denied
find: ‘./home/ubuntu’: Permission denied
find: ‘./home/bandit5/inhere’: Permission denied
find: ‘./home/bandit30-git’: Permission denied
find: ‘./home/drifter8/chroot’: Permission denied
find: ‘./home/drifter6/data’: Permission denied
find: ‘./home/bandit29-git’: Permission denied
find: ‘./home/bandit28-git’: Permission denied
find: ‘./home/bandit27-git’: Permission denied
find: ‘./lost+found’: Permission denied
find: ‘./etc/polkit-1/rules.d’: Permission denied
find: ‘./etc/multipath’: Permission denied
find: ‘./etc/stunnel’: Permission denied
find: ‘./etc/xinetd.d’: Permission denied
find: ‘./etc/credstore.encrypted’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
find: ‘./etc/sudoers.d’: Permission denied
find: ‘./etc/credstore’: Permission denied
find: ‘./dev/shm’: Permission denied
find: ‘./dev/mqueue’: Permission denied
find: ‘./var/log/amazon’: Permission denied
find: ‘./var/log/unattended-upgrades’: Permission denied
find: ‘./var/log/chrony’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/tmp’: Permission denied
find: ‘./var/spool/cron/crontabs’: Permission denied
find: ‘./var/spool/bandit24’: Permission denied
find: ‘./var/spool/rsyslog’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/pollinate’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/cache/apparmor/2425d902.0’: Permission denied
find: ‘./var/cache/apparmor/baad73a1.0’: Permission denied
find: ‘./var/lib/polkit-1’: Permission denied
find: ‘./var/lib/amazon’: Permission denied
./var/lib/dpkg/info/bandit7.password
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/chrony’: Permission denied
find: ‘./var/lib/snapd/void’: Permission denied
find: ‘./var/lib/snapd/cookie’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘./var/lib/udisks2’: Permission denied
find: ‘./var/crash’: Permission denied
find: ‘./boot/efi’: Permission denied
find: ‘./boot/lost+found’: Permission denied
find: ‘./sys/kernel/tracing’: Permission denied
find: ‘./sys/kernel/debug’: Permission denied
find: ‘./sys/fs/pstore’: Permission denied
find: ‘./sys/fs/bpf’: Permission denied
find: ‘./run/lock/lvm’: Permission denied
find: ‘./run/systemd/inaccessible/dir’: Permission denied
find: ‘./run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘./run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘./run/systemd/propagate/chrony.service’: Permission denied
find: ‘./run/systemd/propagate/polkit.service’: Permission denied
find: ‘./run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘./run/systemd/propagate/fwupd.service’: Permission denied
find: ‘./run/systemd/propagate/bolt.service’: Permission denied
find: ‘./run/lvm’: Permission denied
find: ‘./run/log/journal/ec2dd69f90c4a6285216f71caca9bbca’: Permission denied
find: ‘./run/cryptsetup’: Permission denied
find: ‘./run/multipath’: Permission denied
find: ‘./run/screen/S-bandit20’: Permission denied
find: ‘./run/screen/S-bandit27’: Permission denied
find: ‘./run/screen/S-bandit28’: Permission denied
find: ‘./run/screen/S-bandit24’: Permission denied
find: ‘./run/screen/S-bandit17’: Permission denied
find: ‘./run/screen/S-bandit12’: Permission denied
find: ‘./run/screen/S-bandit29’: Permission denied
find: ‘./run/screen/S-bandit23’: Permission denied
find: ‘./run/screen/S-bandit1’: Permission denied
find: ‘./run/screen/S-bandit31’: Permission denied
find: ‘./run/screen/S-bandit21’: Permission denied
find: ‘./run/screen/S-bandit22’: Permission denied
find: ‘./run/screen/S-bandit19’: Permission denied
find: ‘./run/screen/S-bandit30’: Permission denied
find: ‘./run/screen/S-bandit33’: Permission denied
find: ‘./run/screen/S-bandit25’: Permission denied
find: ‘./run/screen/S-bandit16’: Permission denied
find: ‘./run/screen/S-bandit0’: Permission denied
find: ‘./run/screen/S-bandit2’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./run/user/11001’: Permission denied
find: ‘./run/user/11013’: Permission denied
find: ‘./run/user/11023’: Permission denied
find: ‘./run/user/11016’: Permission denied
find: ‘./run/user/11028’: Permission denied
find: ‘./run/user/11024’: Permission denied
find: ‘./run/user/11027’: Permission denied
find: ‘./run/user/11015’: Permission denied
find: ‘./run/user/11003’: Permission denied
find: ‘./run/user/11020’: Permission denied
find: ‘./run/user/11032’: Permission denied
find: ‘./run/user/11025’: Permission denied
find: ‘./run/user/11026’: Permission denied
find: ‘./run/user/11021’: Permission denied
find: ‘./run/user/11022’: Permission denied
find: ‘./run/user/11004’: Permission denied
find: ‘./run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘./run/user/11012’: Permission denied
find: ‘./run/user/11011’: Permission denied
find: ‘./run/user/11000’: Permission denied
find: ‘./run/user/11005’: Permission denied
find: ‘./run/user/11008’: Permission denied
find: ‘./run/user/11014’: Permission denied
find: ‘./run/user/11007’: Permission denied
find: ‘./run/user/11002’: Permission denied
find: ‘./run/user/11009’: Permission denied
find: ‘./run/user/11010’: Permission denied
find: ‘./run/user/11019’: Permission denied
find: ‘./run/user/8003’: Permission denied
find: ‘./run/user/8001’: Permission denied
find: ‘./run/user/11017’: Permission denied
find: ‘./run/user/11033’: Permission denied
find: ‘./run/user/8002’: Permission denied
find: ‘./run/chrony’: Permission denied
find: ‘./run/udisks2’: Permission denied
bandit6@bandit:/$ cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
# Level 7
This was fairly simple, all i had to do was to use the grep command on data.txt to find the password.<br>
```bash
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
# Level 8
Learnt the `sort` and `uniq` command and with their help was able to reach to the desired password.<br>
```bash
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ cat data.txt | sort | uniq -c
     10 0BKVRLEJQcpNx8wnSPxDLFnFKlQafKK6
     10 0eJPctF8gK96ykGBBaKydhJgxSpTlJtz
     10 0kJ7XHD4gVtNSZIpqyP1V45sfz9OBLFo
     10 0lPOvKhpHZebxji0gdjtGCd5GWiZnNBj
     10 0REUhKk0yMqQOwei6NK9ZqIpE5dVlWWM
     10 1jfUH1m4XCjr7eWAeleGdaNSxFXRtX0l
     10 1VKPEkd0bCtIRwMFVQfY7InulwOFyDsn
     10 2u8fvAzvnaFlvQG3iPt4Wc1TFhPcGxhH
     10 35l6mr3f6TvlJyDwU6aUgJX07cLhr6t9
     10 3FIgajXBiaQAiTMVGo1gxRDSiACNyvvJ
     10 3mNA2le0gfURQKNHVIhGkMNLqLwjyyLN
      1 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
     10 4P8FsHcdr7d5WKnPtAaXY5SslKICd2gL
     10 5EmwMKZHwF6Lwq5jHUaDlfFJBeHbcX0b
     10 5hYz0028e1Q2TrtPVz5GZbpMzZNjebhh
     10 5I2jWpqjtVp576xXI2TLh1UCyXJtGQ78
     10 6Boy6esAjnIxCYn8uI6KZ7VD7zysDM8i
     10 7cP8ssLElERHXqOJc9T84bxsmJBjNXk2
     10 7qHmEo1FEbzthgyNpKc38YofXjYKZv18
     10 8FCtUQlFXsJnNeyiDY5KfE3vRy6sZFEJ
     10 8pePxslMzXqA2mi87wFjxd44qDRdrPiW
     10 9jfKbKGp40LjMuiiH9cce4bUo9y8nd0j
     10 9PqZLdu143n5djN9mL1MCamrmHERuV7k
     10 9Tar2wcD3Urge6s2yp18CAE8zX1poUwV
     10 A4MixXbxP5t0RE87qkmAdwwPJO3Aw6rO
     10 aFStfHbnQdPWqyRHEzhqe91Wch4O8xHJ
     10 aMKlTMrptUxxTypCHocCTrqYRkR2gT8h
     10 AOz67fZdaabu2QQyatGXK1dXNUIuyuOD
     10 BIAd2jxKMFmitEvp0WmsM0oDAwj4WSUa
     10 BmwX4bYhJXyImwt4AVHr7wFyLYCn4IIs
     10 BooZo7QXA1Tft7d6zbVkgJiGoJzuBTXS
     10 ByBO7V0FaYWN1cqIFbNss21xmjf9VNBP
     10 CgUjZiluCoMEvzNAge1Nbv3g9tpLQQj2
     10 CgvfWFmg5yxx12D2SZvjzaakG0JIyg7B
     10 cOk5XehQn4Uoz1z255BqS8y74pthqBeC
     10 dPk8jhZUckmUiDsn4fXE28LpV5VTvev7
     10 DShzsMw0ejGwWSFIlvAybLwBLKX6qVfF
     10 EgKFNgP4k1pMfGdrWRSiDIvSlAC0Tr42
     10 EtevhzigGTVT4NbybBWK5DNXnPt2D5AM
     10 fmt1Bzwt8Yw0t0cBVine7zuwyS76iJ7N
     10 fSbQqHX7C5Er4WmMSlQ9jkl05sXYQgJU
     10 ft7OpREehafXGOiX8EtyzEqXU8f3KRug
     10 GCaJbpW4K28ukFR84YhZFY6e7MvAOwpX
     10 GW8cRcKbnz53MAPYECx99O0T8POlPIFk
     10 hevU1VzF39ZyhyYkCBgmVrY6DbiRt2t5
     10 HloFLs5IpuFLuVJugBxKEipr5QaObJMk
     10 iGmmKP7APsDfPxrZjCL7eDpGEWR3ot3q
     10 IkJadTScIdBQY9a4KVjBEHyXKubCxSlx
     10 JaFwKSH0hiff1XRuxVYCzjjtibV9P3zF
     10 JQx6RCcNbAesB2lehrUl821WnJPI5gHW
     10 K8GxBwF1vxLQB5PaqlcCGfRniemRScj4
     10 kgf5CWCm26sycUzaAJRP7e6hYKVwu7Y4
     10 KhRNo5JlbDhxbBqCGIokXqBm54v7Wunm
     10 KqpxKPY3yIDdEVewIwuetpV0WvGIsN5U
     10 KZJOZECxhLxDhxDbGzdNy8m0uplzvP11
     10 L2iewY0lmIRR6arfrwWA3VhttgbJ0NIn
     10 mMD5Z4y1rRh07rmVRw2HfgcMegbKH0c0
     10 mUNISmDjtb3h6xAt3wGRVTY9U0r2u9bR
     10 noa4sUvodI8D733ugvy2OAlttHdjMPWJ
     10 o44oO4jbyPqoQQYX16586yC7Os2uz3ks
     10 omBfcRI91Zm06GI0RLngq05AMwe8Ndqo
     10 PHE4soLmy3nZfNOlX3jB8LYKYZRXuTah
     10 pij5cPffIOml4tkDCOwo7M2zyxImYJWm
     10 PLsGPuNgYzI8YNu2Y7h4D4vz1nHPSuNl
     10 pngaDVKjQWnWHOOUze15L3QpwqKme5M9
     10 PRerp5EfTVxJHKuCZDXfAfRyCQSdPjMi
     10 prq3SdTnv0vUMlcfcb4yvkl6GAXvtwWE
     10 q3dcRUh6vecqwa2ahKdvwWJDon3qA1Xe
     10 qEi18Iw0qI0fe3fGMr6tTPpL6SbPMjk3
     10 QPVchwY9MCJJ1W6kCWMncGWK2YfcUlFE
     10 QQozajTq9wdmrO8AMwcL1i4EG0DA3I3a
     10 QWumJVhaTjgcTVU6PILDgf5nPauD4VMm
     10 RAM7lFRXtvR3BlgtbRU3dz5UxZYQQ06I
     10 RAp5mFyjEBVSRTU203Y4Q1RDSlj7hN1v
     10 rENclsy8XIuTnTvJfXagTFpcd78FX8WM
     10 rhquEZ5rMuUSRIxtG9DQ6KVOyqPpL0MP
     10 RpRE5maDwMQTa8oJt7vVNqff7ElrjLTq
     10 s8SnoFuk0jR1CTdQ7pctd67nakJWN2Vc
     10 sapgezVFdEYdD3IkqFZGaXcKG4z5P4KR
     10 sBDaWzvCbXUiXcP9to4j8o716bXI0inx
     10 SCuPKgJN6pAfwgoCy2Ech2U0DTfriL9q
     10 Sd14OpeUCugURrfuu47xRwMGB1U6OSzB
     10 SeSKZp3f2Lo9JAKP17WmkD2Nnl6I5knE
     10 SnF0df244Nioa8VK7fAC8dfc9jQpAx4Y
     10 Su9w1lri9UACf53cL1evAMKXVgI0nfqe
     10 tgHSfEXcbYCejWXfsWDO4VXXbqtTVcqS
     10 tVm8L7CmsGG0cox6GpzlkbQYl0Yavx6i
     10 ULGqvJWOAtmPYINByDHwD0r9Mlf5niGK
     10 UuNP4xguSOjcTHAzdtHBgm2eNz1Z5133
     10 VPlmPWbTDtWppKumxNRUeeXklDk5GpRx
     10 w6x5XtaoRWDqMCsYxgZIWuOKVdiGByAu
     10 wcX8FCnaWngvBoYa5LrRlDsfRrr3C4kv
     10 Wr4hWlUhGCKJpGDCeio8C1pLVt7DZm3X
     10 WVQJq1JYFGgtR69JgWxUAKPb0RaKc90J
     10 xEkmXBLggW8r1alEgwNX6ZIM6GGCsfmF
     10 YbfaJNckJrgh9TvEBScUaEUCRhDJcgIL
     10 ylbAYB5vBiEAmViEQOBwITUwjSZkwC7Q
     10 ysKmfYcysVfnViisRBcXzgjjXMDgnKKv
     10 YZMapJFORxWg84gej4UzQvGYSqBmsPOo
     10 Z6SdYkOf5loRVj4uRk6cNiz10RfPnwNy
     10 zokSjnkcDj1hdGEBE4feukfCtFmv82ZZ
```
# Level 9
It was told that the password was among the some human readable files so i learnt about the `strings` command and piped its output to grep and found the pass.<br>
```bash
bandit9@bandit:~$ strings data.txt | grep =
}========== the
p\l=
;c<Q=.dEXU!
3JprD========== passwordi
qC(=
~fDV3========== is
7=oc
zP=
~de=
3k=fQ
~o=0
69}=
%"=Y
=tZ~07
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
N=~[!N
zA=?0j
```
# Level 10
Learnt about the `base64` command and how it can be used to encode and decode data in base64 format.<br>
```bash
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
bandit10@bandit:~$
```
