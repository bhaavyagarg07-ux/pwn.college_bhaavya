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



