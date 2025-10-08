# Perceiving Permission


## Changing file ownership
change the owner of the /flag file to the hacker user, and then read the flag

### Solve
**Flag** `pwn.college{8zhpsvAAedXu8p9rpS518D344xK.QXxEjN0wSN0kjNzEzW}`

```bash
chown hacker /flag
pwn.college{8zhpsvAAedXu8p9rpS518D344xK.QXxEjN0wSN0kjNzEzW}
```
### New Learnings
using chown we can change the ownership of file.

### Refrences
Challenge Description


## Groups and Files
change the group who can access the flag file from root to hacker

**Flag** `pwn.college{MW1LdZcXJmBHho_BQPNndq7aVPg.QXxcjM1wSN0kjNzEzW}`

```bash
ls -l
chgrp hacker not-the-flag
cat not-the-flag
pwn.college{MW1LdZcXJmBHho_BQPNndq7aVPg.QXxcjM1wSN0kjNzEzW}
```
### New Learnings
using chgrp we can change the group of files

### Refrences
Challenge Description




