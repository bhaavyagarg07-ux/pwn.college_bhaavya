# Pondering PATH

## The PATH Variable 
Disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you

### Solve
**Flag** `pwn.college{81b9-mv8MEEMYFA2EsoEtV_fwAE.QX2cDM1wSN0kjNzEzW}`

```bash
PATH=" "
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: command not found
The flag is still there! I might as well give it to you!
pwn.college{81b9-mv8MEEMYFA2EsoEtV_fwAE.QX2cDM1wSN0kjNzEzW}
```
### New Learnings
learned about PATH command. kept the path empty so that the rm could not be found upon rinning /challenge/run

### Refrences
desrciption of the challenge



## Setting Path
set path to the given directory and run /challenge/run

### Solve
**Flag** `pwn.college{wRGvUPw3vMtW-mLyR71VAQXN0WY.QX1cjM1wSN0kjNzEzW}`

```bash
hacker@path~setting-path:~$ PATH="/challenge/more_commands"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{wRGvUPw3vMtW-mLyR71VAQXN0WY.QX1cjM1wSN0kjNzEzW}
```
### New Learnings
practiced more on path command

### Refrences
desrciption of the challenge



## Finding command
find the path of win command and cat flag

### Solve
**Flag** `pwn.college{8ABwPzPjxnbl0p7_YxrJwOS9TLw.01NzEzNxwSN0kjNzEzW}`

```bash
which win
/challenge/paths/8792/win
hacker@path~finding-commands:~$ cat /challenge/paths/8792/win
#!/bin/bash

/bin/fold -s <<< "Search for the flag in the same directory in which I am located!"
hacker@path~finding-commands:~$ cd /challenge/paths/8792
hacker@path~finding-commands:/challenge/paths/8792$ cat win
#!/bin/bash

/bin/fold -s <<< "Search for the flag in the same directory in which I am located!"
hacker@path~finding-commands:/challenge/paths/8792$ cat flag
pwn.college{8ABwPzPjxnbl0p7_YxrJwOS9TLw.01NzEzNxwSN0kjNzEzW}
```
### New Learnings
using which command we can find out the path of thst command

### Refrences
desrciption of the challenge



## Adding commands
make a shell script called win, add its location to the PATH, and enable /challenge/run to find it

### Solve
**Flag** ``

```bash
 echo 'cat /flag' > win
hacker@path~adding-commands:~$ PATH=":$PATH"
hacker@path~adding-commands:~$ chmod a+x win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{gf2GNh-hSOAjw_PZQXJKjdek3Rz.QX2cjM1wSN0kjNzEzW}
```
### New Learnings
adding commands while old commands stays the same

### Refrences
desrciption of the challenge


## Hijacking Commands
Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you.
How can you solve this? You know that rm is searched for in the directories listed in the PATH variable. You have experience creating the win command when the previous challenge needed it.


### Solve
**Flag** `pwn.college{wi35Q2sdvLY1n6I62R_wR_XficQ.QX3cjM1wSN0kjNzEzW}`

```bash
hacker@path~hijacking-commands:~$ echo '#!/bin/bash' > /tmp/rm
hacker@path~hijacking-commands:~$ echo 'cat /flag' >> /tmp/rm
hacker@path~hijacking-commands:~$ chmod +x /tmp/rm
hacker@path~hijacking-commands:~$ export PATH="/tmp:$PATH"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /tmp/rm. Executing!
pwn.college{wi35Q2sdvLY1n6I62R_wR_XficQ.QX3cjM1wSN0kjNzEzW}
```
### New Learnings
when /challenge/run invoked rm it found /tmp/rm before /bin/rm the actual rm file

### Refrences
desrciption of the challenge
