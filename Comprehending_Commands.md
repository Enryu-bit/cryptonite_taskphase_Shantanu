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
## Hidden Files
Learnt that not all files are visible when `ls` is used and files that are preceded by `.` are hidden. <br>
To view the hidden files i used the `ls -a` command.<br>
There was a sus file named `.flag---`.<br>
I tried to run it by `/.flag--`but it showed access denied.<br>
So i used the `cat` command to read the flag out of it.<br>
```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.                      bin        etc    lib64   nix   run   tmp
..                     boot       home   libx32  opt   sbin  usr
.dockerenv             challenge  lib    media   proc  srv   var
.flag-210942113927702  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:/$ cat .flag-210942113927702
pwn.college{MmRY9oXc3rD-lackXvYw2ec-bDT.dBTN4QDLzYTN0czW}
```
## An Epic Filesystem Quest
In this we had to show our proficiency in using `cat`,`ls` and `cd` commands.<br>
There were some conditions to be met otherwise the files would self destruct but it was fairly easy.<br>
Files were hidden, some had conditions to only access from directory or some had not going in the directoy.<br>
Finally After a series of `cd` `cat` and `ls` i was finally able to get the flag.<br>
```bash
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.           SPOILER  challenge  flag  lib32   media  opt   run   sys  var
..          bin      dev        home  lib64   mnt    proc  sbin  tmp
.dockerenv  boot     etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat SPOILER
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/drivers/infiniband/hw/mlx5

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/drivers/infiniband/hw/mlx5
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/infiniband/hw/mlx5$ ls -a
.        Makefile  cong.c      flow.c    ib_virt.c  mlx5_ib.h  srq.c
..       ah.c      cq.c        gsi.c     mad.c      mr.c       srq.h
.GIST    cmd.c     devx.c      ib_rep.c  main.c     odp.c      srq_cmd.c
Kconfig  cmd.h     doorbell.c  ib_rep.h  mem.c      qp.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/infiniband/hw/mlx5$ cat >G
ssh-entrypoint: G: Permission denied
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/infiniband/hw/mlx5$ cat .GIST
Great sleuthing!
The next clue is in: /usr/share/vim/vim81/lang/ja.euc-jp
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/infiniband/hw/mlx5$ cd /usr/share/vim/vim81/lang/ja.euc-jp
hacker@commands~an-epic-filesystem-quest:/usr/share/vim/vim81/lang/ja.euc-jp$ ls -a
.  ..  LC_MESSAGES  SNIPPET
hacker@commands~an-epic-filesystem-quest:/usr/share/vim/vim81/lang/ja.euc-jp$ cat SNIPPET
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/tools/power/x86/turbostat

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/vim/vim81/lang/ja.euc-jp$ cd /opt/linux/linux-5.4/tools/power/x86/turbostat
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/x86/turbostat$ ls -a
.  ..  .WHISPER  .gitignore  Makefile  turbostat.8  turbostat.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/x86/turbostat$ cat .WHISPER
Tubular find!
The next clue is in: /usr/share/racket/pkgs/redex-benchmark/redex/benchmark/models/compiled

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/x86/turbostat$ cd /usr/share/racket/pkgs/redex-benchmark/redex/benchmark/models/compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/redex-benchmark/redex/benchmark/models/compiled$ ls -a
.   .REVELATION       all-info_rkt.zo        type-all-info_rkt.zo
..  all-info_rkt.dep  type-all-info_rkt.dep
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/redex-benchmark/redex/benchmark/models/compiled$ cat .REVELATION
Tubular find!
The next clue is in: /opt/linux/linux-5.4/arch/csky/boot

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/redex-benchmark/redex/benchmark/models/compiled$ cd
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/arch/csky/boot/LEAD-TRAPPED
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/scipy/optimize/_shgo_lib

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/lib/python3/dist-packages/scipy/optimize/_shgo_lib
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/_shgo_lib$ ls
INFO  __init__.py  __pycache__  sobol_seq.py  sobol_vec.gz  triangulation.py
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/_shgo_lib$ cat INFO
Lucky listing!
The next clue is in: /opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/_shgo_lib$ cd /opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ ls
README                                dep-build-script-build-script-build
build-script-build-script-build       invoked.timestamp
build-script-build-script-build.json
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cat README
Great sleuthing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/scapy/modules/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/kropr/target/release/.fingerprint/thiserror-d63aee1970f751e8$ cd /usr/local/lib/python3.8/dist-packages/scapy/modules/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/scapy/modules/__pycache__$ ls
DOSSIER                  p0f.cpython-38.pyc       voip.cpython-38.pyc
__init__.cpython-38.pyc  p0fv2.cpython-38.pyc
nmap.cpython-38.pyc      ticketer.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/scapy/modules/__pycache__$ cat DOSSIER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{U97tTQ11qz9ewYuGG3zZC3nFgK3.dljM4QDLzYTN0czW}
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/scapy/modules/__pycache__$
```
## Making Directories
In this I learnt how to use the `mkdir` command and make a directory named `pwn` in tmp directory.<br>
Then I used `touch` to create a file named `college`.<br>
Then used `/challenge/run` to get the flag.<br>
```bash
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  tmp.MiOQGWw5Zc
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ ls
college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{snB8XU63Z2y_K2aym4UzZBR9kDg.dFzM4QDLzYTN0czW}
```
