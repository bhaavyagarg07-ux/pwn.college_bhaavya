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



