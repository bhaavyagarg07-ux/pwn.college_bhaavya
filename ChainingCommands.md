# Chaining Commands

## Chaining with semicolon
run 2 commands by chaining with ;

### Solve
**Flag** `pwn.college{wR3wE4_8uFjyTBxtnn44dBtxiRl.QX1UDO0wSN0kjNzEzW}`

```bash
/challenge/pwn; /challenge/college
pwn.college{wR3wE4_8uFjyTBxtnn44dBtxiRl.QX1UDO0wSN0kjNzEzW}
```
### New Learnings
we can run multiple commands at once by chaining them with ;

### Refrences
desrciption of the challenge


## Building on successs
run 2 commands by chaining with &&

### Solve
**Flag** ` pwn.college{clSLYAXPNohua8RLR-NltregzHq.0lM0MDOxwSN0kjNzEzW}`

```bash
/challenge/first-suscess &&/challenge/second
 pwn.college{clSLYAXPNohua8RLR-NltregzHq.0lM0MDOxwSN0kjNzEzW}
```
### New Learnings
we can run multiple commands at once by chaining them with && when first commands excecutes successly then only it chains with the second one

### Refrences
desrciption of the challenge


## Handling Failure
run 2 commands by chaining with ||

### Solve
**Flag** `pwn.college{8ZhfqQ-wQ-cSGcFp4ntDjxTEPnZ.01M0MDOxwSN0kjNzEzW}`

```bash
/challenge/first-failure || /challenge/second
 pwn.college{clSLYAXPNohua8RLR-NltregzHq.0lM0MDOxwSN0kjNzEzW}
```
### New Learnings
we can run multiple commands at once by chaining them with && when first commands fails then only it chains with the second one

### Refrences
desrciption of the challenge


## Your first shell script
run 2 commands by chaining with ||

### Solve
**Flag** ` pwn.college{clSLYAXPNohua8RLR-NltregzHq.0lM0MDOxwSN0kjNzEzW}`

```bash
echo /challenge/pwn > x.sh
echo /challenge/college >> x.sh
bash x.sh
pwn.college{MvntXjMrRT4hE0BfSFXdV7WiLNE.QXxcDO0wSN0kjNzEzW}
```
### New Learnings
learned how to make a shell script 

### Refrences
desrciption of the challenge



## Redirecting Script Output
run 2 commands by chaining with ||

### Solve
**Flag** `pwn.college{c-C2-vx80gfdQ9CU0d5BegQHcpP.QX4ETO0wSN0kjNzEzW}`

```bash
echo /challenge/pwn > x.sh
echo /challenge/college >> x.sh
bash x.sh | /challenge/solve
pwn.college{c-C2-vx80gfdQ9CU0d5BegQHcpP.QX4ETO0wSN0kjNzEzW}
```
### New Learnings
learned how to pipe the output of a shell script into another program

### Refrences
desrciption of the challenge



## Redirecting Script Output
make a shell script with /challenge/solve and run it without bash

### Solve
**Flag** `pwn.college{YM_1F3BTiyS8dDgSPSYxdGOe28L.QX0cjM1wSN0kjNzEzW}`

```bash
echo /challenge/solve > x.sh
./x.sh
ls -l x.sh
chmod a+x x.sh
./x.sh
pwn.college{YM_1F3BTiyS8dDgSPSYxdGOe28L.QX0cjM1wSN0kjNzEzW}
```
### New Learnings
we can directly run a shell from home directory

### Refrences
desrciption of the challenge



## Understanding Shebangs
make a shell script with /challenge/solve and run it without bash

### Solve
**Flag** `pwn.college{YM_1F3BTiyS8dDgSPSYxdGOe28L.QX0cjM1wSN0kjNzEzW}`

```bash
 echo '#!/bin/bash' > /home/hacker/solve.sh
echo 'echo "hack the planet"' >> /home/hacker/solve.sh
chmod a+x /home/hacker/solve.sh
/challenge/run
Flag: pwn.college{IQ8p3V9aIFZ_YejqHCVPqcpe5rG.0VOzMDOxwSN0kjNzEzW}
```
### New Learnings
learned to use shebangs. we created a executable file /bin/bash so that the terminal knows to run the file with bash.

### Refrences
desrciption of the challenge


## Script with Arguments 
For this challenge, you need to write a script at /home/hacker/solve.sh that:
Takes two arguments
Outputs them in REVERSE order (second argument first, then the first argument)
after than run /challenge/run
### Solve
**Flag** `pwn.college{A4-RBZDsIMILENmt7vXRmC1WOWr.0VNzMDOxwSN0kjNzEzW}`

```bash
echo '#!/bin/bash' > /home/hacker/solve.sh
echo 'echo "$2 $1"' >> /home/hacker/solve.sh
/challenge/run
pwn.college{A4-RBZDsIMILENmt7vXRmC1WOWr.0VNzMDOxwSN0kjNzEzW}
```
### New Learnings
learned about arguments

### Refrences
desrciption of the challenge


## Scripting with conditions
write a scrift that prints college if the inpu is pwn

### Solve
**Flag** `pwn.college{gaNTdylSSmhUX1Wf1mOi-SJYzcp.0lNzMDOxwSN0kjNzEzW}`

```bash
echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'if [ "$1" = "pwn" ]
> then
> echo college
> fi ' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{gaNTdylSSmhUX1Wf1mOi-SJYzcp.0lNzMDOxwSN0kjNzEzW}
```
### New Learnings
learned if then fi commands and practiced more on scripting

### Refrences
desrciption of the challenge



## Scripting with default cases
write a scrift that prints college if the input is pwn and nope for all other input

### Solve
**Flag** `pwn.college{Yopw68F6qIjW625zmdA2_l9-iyB.01NzMDOxwSN0kjNzEzW}`

```bash
 echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'if [ "$1" = "pwn" ]
then
echo college
else
echo nope
fi ' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{Yopw68F6qIjW625zmdA2_l9-iyB.01NzMDOxwSN0kjNzEzW}
```
### New Learnings
learned if then else fi commands and practiced more on scripting

### Refrences
desrciption of the challenge



## Scripting with multiple conditions
write a scrift that prints college if the input is pwn input learn output linux and unknown for all other cases

### Solve
**Flag** `pwn.college{EeGlFqaXFNnaSOd6m16PbtVofkV.0FOzMDOxwSN0kjNzEzW}`

```bash
 echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'if [ "$1" = "hack" ]
> then
> echo "the planet"
> elif [ "$1" == "pwn" ]
> then
> echo college
> elif [ "$1" == "learn" ]
> then
> echo linux
> else
> echo unknown
> fi ' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{EeGlFqaXFNnaSOd6m16PbtVofkV.0FOzMDOxwSN0kjNzEzW}
```
### New Learnings
learned if then elif else fi commands and practiced more on scripting

### Refrences
desrciption of the challenge



## Reading shell scripts 
read a script and find password and run /challenge/run
### Solve
**Flag** `pwn.college{snCQRcw6CthU7_gIEqho5LzJuRO.0lMwgDOxwSN0kjNzEzW}`

```bash
cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{snCQRcw6CthU7_gIEqho5LzJuRO.0lMwgDOxwSN0kjNzEzW}
```
### New Learnings
learned to read scripts

### Refrences
desrciption of the challenge
