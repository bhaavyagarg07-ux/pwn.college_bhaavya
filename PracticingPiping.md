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
redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions


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




## Redirecting input
/challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE!


### Solve
**Flag** `pwn.college{0VmZ-Lz8ruJaERkBRRVMzuaG-Iq.QXwcTN0wSN0kjNzEzW}`

```bash
COLLEGE < PWN
echo COLLEGE > PWN
/challenge/run < PWN
pwn.college{0VmZ-Lz8ruJaERkBRRVMzuaG-Iq.QXwcTN0wSN0kjNzEzW}
```
### New Learnings
using < we can redirect input



## Grepping stored values
redirect the output from /challenge/run to /tmp/data.txt and grep the flag


### Solve
**Flag** `pwn.college{UHoTaB0Nw3-emFy6-3i96PotYSf.QX4EDO0wSN0kjNzEzW}`

```bash
/challenge/run > /tmp/data.txt
grep flag /tmp/data.txt
cat flags
grep pwn.college /tmp/data.txt
pwn.college{UHoTaB0Nw3-emFy6-3i96PotYSf.QX4EDO0wSN0kjNzEzW}
```
### New Learnings
practiced more on grepping and redirecting





## Grepping live output
/challenge/run will give output to hundered's of flag grep out the real flag


### Solve
**Flag** `pwn.college{UEOA0Tje53K_WxbSBpS0mcPRslO.QX5EDO0wSN0kjNzEzW}`

```bash
/challenge/run | grep pwn.college
pwn.college{UEOA0Tje53K_WxbSBpS0mcPRslO.QX5EDO0wSN0kjNzEzW}
```
### New Learnings
practiced more on grepping 



## Grepping errors
grep through error to find the flag

### Solve
**Flag** `pwn.college{omRIz43skX8ACjAF9sM6EEm5arD.QX1ATO0wSN0kjNzEzW}`

```bash
/challenge/run 2>&1 | grep pwn.college
pwn.college{omRIz43skX8ACjAF9sM6EEm5arD.QX1ATO0wSN0kjNzEzW}
```
### New Learnings
using >& we can redirect the file description to another file so we first redirected the standard errror to standerd output and piped it

### Refrences
https://www.geeksforgeeks.org/linux-unix/piping-in-unix-or-linux/


## Filtering with grep
use grep -v to filter out the flags with the word DECOY

### Solve
**Flag** `pwn.college{oMtvWvRDW-gomqklwK-0_ipX9O2.0FOxEzNxwSN0kjNzEzW}`

```bash
 /challenge/run | grep -v DECOY
pwn.college{oMtvWvRDW-gomqklwK-0_ipX9O2.0FOxEzNxwSN0kjNzEzW}
```
### New Learnings
using grep -v we can filter out the outputs 


## Duplicating piped data with tee
/challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs

### Solve
**Flag** `pwn.college{IC7NgOEykALLlCs9IrBkTEMhRZH.QXxITO0wSN0kjNzEzW}`

```bash
/challenge/pwn | tee fl | /challenge/college
cat fl
/challenge/pwn --secret IC7NgOEy
/challenge/pwn --secret IC7NgOEy | tee fl | /challenge/college
pwn.college{IC7NgOEykALLlCs9IrBkTEMhRZH.QXxITO0wSN0kjNzEzW}
```
### New Learnings
using tee we can duplicate data it reads standard input and simultaneously reads it to standard output. just like the t pipe in plumbing. here if we did not tee it the output of command 1 would be the input to command 2 but using tee we can see the output of command 1 and find errors if any and modify accordingly

### Refrences
https://www.geeksforgeeks.org/linux-unix/tee-command-linux-example/



## Process substitution for input
using diff command and process substituion find the flag

### Solve
**Flag** `pwn.college{oon9vGo8eFndzRpQ-mG5HBEwPpN.0lNwMDOxwSN0kjNzEzW}`

```bash
diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
pwn.college{oon9vGo8eFndzRpQ-mG5HBEwPpN.0lNwMDOxwSN0kjNzEzW}
```
### New Learnings
using process substition we can treat output of commands or commands as if they were files. 



## Writing to multiple programs
Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands

### Solve
**Flag** `pwn.college{Ix29fpHx3SKq-CkYYhdcfIf05hx.QXwgDN1wSN0kjNzEzW}`

```bash
/challenge/hack | tee >(/challenge/the) >(/challenge/planet)
pwn.college{Ix29fpHx3SKq-CkYYhdcfIf05hx.QXwgDN1wSN0kjNzEzW}
```
### New Learnings
tee stored the output of /hack and stored it to 3 diff places stdout /planet and /the


## split piping stderr and stdout
In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program

### Solve
**Flag** `pwn.college{QnLzuJt7g1nQLFDNL7KVTRhWG-W.QXxQDM2wSN0kjNzEzW}`

```bash
challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
pwn.college{QnLzuJt7g1nQLFDNL7KVTRhWG-W.QXxQDM2wSN0kjNzEzW}
```
### New Learnings
/planet gets the stdout from /hack and /the hets the stderr from /hack


## split piping stdr and stdout
In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program

### Solve
**Flag** `pwn.college{QnLzuJt7g1nQLFDNL7KVTRhWG-W.QXxQDM2wSN0kjNzEzW}`

```bash
challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
pwn.college{QnLzuJt7g1nQLFDNL7KVTRhWG-W.QXxQDM2wSN0kjNzEzW}
```
### New Learnings
/planet gets the stdout from /hack and /the hets the stderr from /hack
the first > is redirection and second > is process substitution




## Named Pipes
create a /tmp/flag_fifo file and redirect the stdout of /challenge/run to it. If you're successful, /challenge/run will write the flag into the FIFO

### Solve
**Flag** `pwn.college{0ZkvExOgmG2-dtJa-9fCWer7Dp1.01MzMDOxwSN0kjNzEzW}`

```bash
mkfifo /tmp/flag_fifo(T1)
cat /tmp/flag_fifo(T1)
/challenge/run > /tmp/flag_fifo(T2)
pwn.college{0ZkvExOgmG2-dtJa-9fCWer7Dp1.01MzMDOxwSN0kjNzEzW}
```
### New Learnings
T1 and T2 specify diffferent terminals
FIFO required two terminals 
the  ormal pipe is unnamed and is temporary while a fifo or named pipe can exist longer untill deleted
using mkfifo we can craete a fifo

### REfrences
https://www.geeksforgeeks.org/cpp/named-pipe-fifo-example-c-program/
