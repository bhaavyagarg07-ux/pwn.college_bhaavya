# Practicing Piping


## Redirecting output
use output redirection to write word pwn to the file college 


### Solve
**Flag** `pwn.college{ci4ElnrU9l5d2_fSa7CeK00rJgB.QX0YTN0wSN0kjNzEzW}`

```bash
echo PWN > COLLEGE
pwn.college{ci4ElnrU9l5d2_fSa7CeK00rJgB.QX0YTN0wSN0kjNzEzW}
```
### New Learnings
using > we can redirect output using echo command
eg echo my name is bhaavya > README.md
my name is bhaavya will be typed to the file

## Redirecting more output
the flag is in /challenge/run redirect it to myflag file and cat the myflag


### Solve
**Flag** `pwn.college{YUz7EV4krH8mcDt7QIxuTGTd5w5.QX1YTN0wSN0kjNzEzW}`

```bash
/challenge/run > myflag
cat myflag
pwn.college{YUz7EV4krH8mcDt7QIxuTGTd5w5.QX1YTN0wSN0kjNzEzW}
```
### New Learnings
using > we can redirect output using paths and files



