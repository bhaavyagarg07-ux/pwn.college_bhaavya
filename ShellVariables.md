# Shell Variables

## Printing Variables
print out the flag variable 

### Solve
**Flag** ``

```bash
echo $FLAG
pwn.college{Y8IOyiSeKIN4qdpY5y3J-Jdw8K9.QX3UTN0wSN0kjNzEzW}
```
### New Learnings
using echo$ we can get the output of variable

### Refrences
challenge description 


## Setting Variables
assign COLLEGE value to the variable PWN

### Solve
**Flag** `pwn.college{EtzNzW8mLXjjOECCUh5osvd9z2r.QX5UTN0wSN0kjNzEzW}`

```bash
PWN=COLLEGE
pwn.college{EtzNzW8mLXjjOECCUh5osvd9z2r.QX5UTN0wSN0kjNzEzW}
```
### New Learnings
using =$ we can assign value to variable

### Refrences
challenge description 


## Multi word Variables
assign COLLEGE YEAH value to the variable PWN

### Solve
**Flag** `pwn.college{sMARszvqsfyqu0_bWH4BGgGqZ35.QXwYTN0wSN0kjNzEzW}`

```bash
PWN="COLLEGE YEAH"
pwn.college{sMARszvqsfyqu0_bWH4BGgGqZ35.QXwYTN0wSN0kjNzEzW}
```
### New Learnings
using " " we can assign multi word value to variable

### Refrences
challenge description 




## Exporting Variables
invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported

### Solve
**Flag** `pwn.college{cD7hFjtd8DYOKvCB4GNPlwMTG4f.QXyYTN0wSN0kjNzEzW}`

```bash
PWN=COLLEGE
COLLEGE=PWN
/challenge/run
export PWN
/challenge/run
pwn.college{cD7hFjtd8DYOKvCB4GNPlwMTG4f.QXyYTN0wSN0kjNzEzW}
```
### New Learnings
first pwn and college both were shell variable and hence /challenge/run did not work when export pwn did it became environment variable and hence was available for the child process /challenge/run




## Printing Exported Variables
use env  command it will print out every exported variable find the flag

### Solve
**Flag** `pwn.college{g5QklHOqelGowouKwz7Ajwr0O2h.QX4UTN0wSN0kjNzEzW}`

```bash
env
pwn.college{g5QklHOqelGowouKwz7Ajwr0O2h.QX4UTN0wSN0kjNzEzW}
```
### New Learnings
using env we can print every exported variable

### Refrences
challenge description 



## Sorting Commands Output
Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag

### Solve
**Flag** `pwn.college{8ccRDOyYhGnm2i_gEJ9QZ1zzpDF.QX1cDN1wSN0kjNzEzW}`

```bash
PWN=$(/challenge/run)
pwn.college{8ccRDOyYhGnm2i_gEJ9QZ1zzpDF.QX1cDN1wSN0kjNzEzW}
```
### New Learnings
we can read output from the file directly and store then in the variable using $()

### Refrences
challenge description 



## Reading Inputs
read the input of PWN variable as COLLEGE

### Solve
**Flag** `pwn.college{wlFwnRWCQDaScOXVNNn2W2cP5gq.QX4cTN0wSN0kjNzEzW}`

```bash
read -p "enter input" PWN
enter input COLLEGE
pwn.college{wlFwnRWCQDaScOXVNNn2W2cP5gq.QX4cTN0wSN0kjNzEzW}
```
### New Learnings
using read comand we can read the input using -p argument we can specify a propt message

### Refrences
challenge description 

## Reading files
read /challenge/read_me into the PWN environment variable, and we'll give you the flag

### Solve
**Flag** `pwn.college{ocMJuEKzoDrJt42tY5AGX8_YfAJ.QXwIDO0wSN0kjNzEzW}`

```bash
read PWN < /challenge/read_me
pwn.college{ocMJuEKzoDrJt42tY5AGX8_YfAJ.QXwIDO0wSN0kjNzEzW}
```
### New Learnings
we can read the output of a file as a input to the variable. < we redirected the output into the input of PWN variable

### Refrences
challenge description 


