# File Globbing 

## Matching with *
change directory using 8 and then run /chsllenge/run

### Solve
**Flag** `pwn.college{8V8_YXAV-Nr3WB8Fv7lb3s4BRCk.QXxIDO0wSN0kjNzEzW}`

```bash
cd /ch*
/challenge/run
pwn.college{8V8_YXAV-Nr3WB8Fv7lb3s4BRCk.QXxIDO0wSN0kjNzEzW}
```
### New Learnings
learned that * can mean any argument and can be treated as a wild card and replaces the file that match the pattern.


## Matching with ?
change directory to /challenge using ? in place of c and l and then run /challenge/run

### Solve
**Flag** `pwn.college{gSkXPykszHsuZMpg13fSa87tiiq.QXyIDO0wSN0kjNzEzW}`

```bash
cd /?ha??enge
/challenge/run
pwn.college{gSkXPykszHsuZMpg13fSa87tiiq.QXyIDO0wSN0kjNzEzW}
```
### New Learnings
learned that ? can be replaced by any character single character if we need it to be replaced by 2 characters or more we'll use ? that many times

### Refrences
description of challenge


## Matching with []
change directory to /challenge/files and run /challenge/run with single argument for file_b file_a, file_s, and file_h
### Solve
**Flag** `pwn.college{wXn2DUO61Z35YPHa4dtj4nq6KK7.QXzIDO0wSN0kjNzEzW}`

```bash
cd /challenge/files
/challenge/run file[bash]
/challenge/run file_[bash]
pwn.college{wXn2DUO61Z35YPHa4dtj4nq6KK7.QXzIDO0wSN0kjNzEzW}
```
### New Learnings
[] is the wildcard for many characters

### Refrences
description of challenge


## Matching Paths with []
starting from home directory open files in  /challenge/files and run /challenge/run with single argument for file_b file_a, file_s, and file_h 

### Solve
**Flag** `pwn.college{stEqDZT_C1As5u_ATQTkZ6n3PFq.QX0IDO0wSN0kjNzEzW}`

```bash
challenge/run /challenge/files/file_[bash]
pwn.college{stEqDZT_C1As5u_ATQTkZ6n3PFq.QX0IDO0wSN0kjNzEzW}
```
### New Learnings
expand the entire path also using globbing 

### Refrences
description of challenge



## Multiple globs
change directory to /challenge/files and run /challenge/run with single argument for flag file using *

### Solve
**Flag** `pwn.college{MmwFG_N89d6jWiGdL5v1dS2oAOQ.0lM3kjNxwSN0kjNzEzW}`

```bash
cd /challenge/files
cat *p*
ls *p*
/challenge/run
/challenge/run *p*
pwn.college{MmwFG_N89d6jWiGdL5v1dS2oAOQ.0lM3kjNxwSN0kjNzEzW}
```
### New Learnings
learned more about *

### Refrences
description of challenge



## Mixing globs
change directory to /challenge/files and run /challenge/run with single argument of 6 letters for educational challenging pwning

### Solve
**Flag** `pwn.college{0UXUH16mhe9GTjz0H4C-YnuTPf5.QX1IDO0wSN0kjNzEzW}`

```bash
cd /challenge/files
/challenge/run *[ngl]
/challenge/run *i[gl]
/challenge /run [cep]*
pwn.college{0UXUH16mhe9GTjz0H4C-YnuTPf5.QX1IDO0wSN0kjNzEzW}
```
### New Learnings
practiced more on globbing


## Exclusionary globbing
change directory to /challenge/files and run /challenge/run with single argument of 6 letters for files that dont start with p w n
### Solve
**Flag** `pwn.college{MgWaSQ6kAM0er-DDAzY1iXj9Q2C.QX2IDO0wSN0kjNzEzW}`

```bash
cd /challenge/files
/challenge/run [!pwn]*
pwn.college{MgWaSQ6kAM0er-DDAzY1iXj9Q2C.QX2IDO0wSN0kjNzEzW}
```
### New Learnings
learned about [!] it means except those words containing those letters will be displayed as output. its like complimenatry function 1-x types




## Tab completion
without typing cat /challenge/pwncollege using tab key


### Solve
**Flag** `pwn.college{QCYtCKBbYeEjWYgL5JBygYgaT0D.0FN0EzNxwSN0kjNzEzW}`

```bash
cat /challenge/pwn(tab key)
pwn.college{QCYtCKBbYeEjWYgL5JBygYgaT0D.0FN0EzNxwSN0kjNzEzW}
```
### New Learnings
learned that tab key automatically completes the file name directory 



## Tab completion
without typing cat /challenge/pwncollege using tab key


### Solve
**Flag** `pwn.college{QCYtCKBbYeEjWYgL5JBygYgaT0D.0FN0EzNxwSN0kjNzEzW}`

```bash
cat /challenge/pwn(tab key)
pwn.college{QCYtCKBbYeEjWYgL5JBygYgaT0D.0FN0EzNxwSN0kjNzEzW}
```
### New Learnings
learned that tab key automatically completes the file name directory 



## Tab completion
challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p and find the flag


### Solve
**Flag** `pwn.college{YOEAuDRPkUOSR1OsdoBLhXgkoOH.0lN0EzNxwSN0kjNzEzW}`

```bash
ls /challenge/files/pwn
cd /challenge/files
cat pwncollege-hacking
cat pwncollege-flamingo
cat pwn-college
cat pwncollege-flag
pwn.college{YOEAuDRPkUOSR1OsdoBLhXgkoOH.0lN0EzNxwSN0kjNzEzW}
```
### New Learnings
learned that tab key automatically completes the file name directory 
pressing it twice will show all the names



## Tab completion on commands
autocomplete the command pwncollege using tab key

### Solve
**Flag** `pwn.college{gUn8sLl8zmn6dzauYKJjU_y8Dke.0VN0EzNxwSN0kjNzEzW}`

```bash
pwncollege-17160
pwn.college{gUn8sLl8zmn6dzauYKJjU_y8Dke.0VN0EzNxwSN0kjNzEzW}
```
### New Learnings
learned that tab key automatically completes the command also
