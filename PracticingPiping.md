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



## Apending output
run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag which contains half of the flag


### Solve
**Flag** `pwn.college{I4hACWP2n1c-I3E18ND6AS_ICmk.QX3ATO0wSN0kjNzEzW}`

```bash
/challenge/run > /home/hacker/the-flag
stdout >> /home/hacker/the-flag
/challenge/run >> /home/hacker/the-flag
cat /home/hacker/the-flag
pwn.college{I4hACWP2n1c-I3E18ND6AS_ICmk.QX3ATO0wSN0kjNzEzW}
```
### New Learnings
when we use > to redirect output and again use > to redirect output in the same file the previous one gets delted and second one is redirected. we use >> to overwrite the first output


## Redirecting errors
edirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions


### Solve
**Flag** `pwn.college{0G9mRZPMtioknPPbKL-witWzg3R.QX3YTN0wSN0kjNzEzW}`

```bash
/challenge/run > myflag
/challenge/run 2> instructions
/challenge/run > myflag 2> instructions
cat myflag
pwn.college{0G9mRZPMtioknPPbKL-witWzg3R.QX3YTN0wSN0kjNzEzW}
```
### New Learnings
using 2> we can redirect the errors
