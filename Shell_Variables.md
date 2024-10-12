# Shell Variables
## Printing Variables
Learnt about the `echo` command which is used to print out stuff on screen.<br>
It can also print variables by using `$` before their name.<br>
In this challenge the flag was in the variable named `FLAG` and I had to print it out using `echo` command.<br>
```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{cbHm-VwdsuS4mYzQeUwaMFd2_RI.ddTN1QDLzYTN0czW}
```
## Setting Variables
Learnt how to assign values to variables in shell.<br>
`var=1337` note: there should not be a gap after or before `=` or else the shell will treat each segment as a different command.<br>
I also had a doubt regarding the assignment of string values.<br>
The doubt was do i assign the value with a `""` or just normally.<br>
Then I used GFG to address this one.<br>
Reference
`https://www.geeksforgeeks.org/string-manipulation-in-shell-scripting/`.<br>
```bash
hacker@variables~setting-variables:~$ PWN="COLLEGE"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IBFICF6bM_h0a9KPqypgL5k-5GK.dlTN1QDLzYTN0czW}
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IBFICF6bM_h0a9KPqypgL5k-5GK.dlTN1QDLzYTN0czW}
```
## Multi-Word Variables
Learnt the usecase of `" "` and how it can be used to store multiple words inside a variable.<br>
This helps the shell recognize the string inside the `" "` as a single token rather than seperate commands.<br>
Then I used this as instructed by the challenge to get the flag.<br>
```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gQPipLURs32lINqvIF9Ij2KrtxD.dBjN1QDLzYTN0czW}
```
## Exporting Variables
Learnt about scope of variables in shell.<br>
Learnt how by default when variables are created, they are not inherited by the child of the main shell.<br>
we have to use the `export command` to export them to the child shell.<br>
```bash
This concept was fairly simple to understand for me as similar things are there in Java called `Scope of Variables` and thus I had no problem obtaining the flag.<br>
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{AwlTjoQaRdlZZpfWTuQ2oGAbb8p.dJjN1QDLzYTN0czW}
```
## Printing Exported Variables
This was a short challenge and learnt about the `env` command that can be used to read all the exported variables and then `FLAG` can be looked through them.<br>
```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
DOJO_AUTH_TOKEN=29d227b69c77321b11f42e04599d80d2ba0f3a9566c27b392164f4253362ce8f
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:
FLAG=pwn.college{w_simxtNdUXD8VK91h78WE8w-1K.dhTN1QDLzYTN0czW}
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm
LESSOPEN=| /usr/bin/lesspipe %s
SHLVL=1
LC_CTYPE=C.UTF-8
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/run/workspace/bin/env
```
## Storing Command Output
We can store outputs of a command inside variables using `$()`.<br>
This is known as `Command Substitution`.<br>
Older format was using ` ` but this is not advised as it can cause problems in nesting.<br>
In this challenge we had to store the output of `/challenge/run` in a variable called `PWN` and then print it to obtain the flag.<br>
```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{gPc9x_uYdXUf1vA3Km2JIk4-vZa.dVzN0UDLzYTN0czW}
```
