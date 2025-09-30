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

### Refrences
challenge description 
