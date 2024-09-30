# Pondering Paths
## The root
learnt about the tree filesystem in linux. <br>
learnt about what a root(directory) is and how it can contain multiple directories inside it. <br>
the address of the directory is path. <br>
By looking at the path we could trace back to the root. <br>
invoked `/pwn` program to get the flag. <br>
command - `/pwn` <br>
## Program And Absolute Paths
earlier I learnt theory about what directories are, in this challenge I had to access a program by using its path to get the flag <br>
command- `/challenge/run`
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
