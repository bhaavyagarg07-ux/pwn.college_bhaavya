# level 0
ssh -p 2220 bandit0@bandit.labs.overthewire.org

# level 1
```bash
cat readme
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
ssh -p 2220 bandit1@bandit.labs.overthewire.org
```
# level 2
```bash
cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
# level 3
```bash
cat -- '--spaces in this filename--'
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```



# level 4
```bash
 cd inhere
 ls
bandit3@bandit:~/inhere$ ls -a
cat -- '...Hiding-From-You'
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```





# level 5
```bash
 cd inhere
bandit4@bandit:~/inhere$ ls
 cat -- ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```











# level 6
```bash
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19
bandit5@bandit:~/inhere$ find -type f -readable ! -executable -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```





# level 7
```bash
cd /
bandit6@bandit:/$ ls
find -user bandit7 -group bandit6 -size 33c
 cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```



# Level 8
```bash
 cat data.txt | grep millionth
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

