# Process and Jobs

## Listing Processes
we need to look for program running and get the flag by checking the running processes

### Solve
**Flag:** `pwn.college{Igppt9OAc6P1Rpyh4R6N5L9EbHv.QX4MDO0wSN0kjNzEzW}`

```bash
ps -aux |grep challenge
/challenge/26995-run-3910
pwn.college{Igppt9OAc6P1Rpyh4R6N5L9EbHv.QX4MDO0wSN0kjNzEzW}
```

### New Learnings
ps shows process status all the running process 
-f shows full process
-a shows info about all users
-x shows process which are running without a terminal
-u additional info about the process
-e extented information
learned about process sleeping when it said the process was sleeping and the command prompt didnt come it shows that to view a process using ps it was put to sleep in order to maintain the process if it was not done so the process would be killed. and the process did not end the command prompt did not come.

### References 
https://www.geeksforgeeks.org/linux-unix/processes-in-linuxunix/



## Killing Processes
kill /challenge/dont_run and run /challenge/run

### Solve
**Flag:** `pwn.college{EuQcpkyfLmrqSTiB10cXld-NB_M.QXyQDO0wSN0kjNzEzW}`

```bash
ps -aux | grep challenge
kill 136
/challenge/run
pwn.college{EuQcpkyfLmrqSTiB10cXld-NB_M.QXyQDO0wSN0kjNzEzW}
```

### New Learnings
using ps aux i searched for the pid of /challenge/dont_run i used grep so that the challenge is easy to find andd in the challenge description it was used. 
using kill command we can kill a running process
kill only accepts the pid of the process and not the name

### References 
Challenge Description




## Interrupting Processes
run /challenge/run and interrupt it

### Solve
**Flag:** `pwn.college{oIg-3PGls8yscNShn2c-2UYk8VF.QXzQDO0wSN0kjNzEzW}`

```bash
/challenge/run
ctrl C
pwn.college{oIg-3PGls8yscNShn2c-2UYk8VF.QXzQDO0wSN0kjNzEzW}
```

### New Learnings
using ctrl c we can interrupt a running process

### References 
Challenge Description



## Killing Misbehaving Processes
find the decoy program kill it run /challenge/run to get the flag

### Solve
**Flag:** `pwn.college{Y3LHkNlNG6i3zdvRT1O1BR8eZnc.0FNzMDOxwSN0kjNzEzW}`

```bash
ps -aux | grep decoy
kill 142
cat /tmp/flag_fifo
/challenge/run
cat /tmp/flag_fifo
pwn.college{Y3LHkNlNG6i3zdvRT1O1BR8eZnc.0FNzMDOxwSN0kjNzEzW}
```

### New Learnings
a named pipe fifo should have the input and the output in the same line otherwise it blocks the shell

### References 
Challenge Description


## Suspending Processes
run /challenge/run and suspend it

### Solve
**Flag:** `pwn.college{YIQSh9dNVIhocas28Fc0KDNgWFG.QX1QDO0wSN0kjNzEzW}`
```bash
/challenge/run
ctrl z
/challenge/run
pwn.college{YIQSh9dNVIhocas28Fc0KDNgWFG.QX1QDO0wSN0kjNzEzW}
```

### New Learnings
using ctrl z we can suspend a running process

### References 
Challenge Description



## Resuming Processes
run /challenge/run and suspend it and then resume it in the foreground 

### Solve
**Flag:** `pwn.college{047TJ-yxpvakQffEtwC_NV7asFc.QX2QDO0wSN0kjNzEzW}`


```bash
/challenge/run
ctrl z
/challenge/run
fg 
pwn.college{047TJ-yxpvakQffEtwC_NV7asFc.QX2QDO0wSN0kjNzEzW}

```

### New Learnings
using fg command we can resume a suspended process

### References 
Challenge Description


## Backgrounding Processes
run /challenge/run and suspend it and then resume it in the background of the terminal and run its another copy

### Solve
**Flag:** `pwn.college{AlYp7b8sHukKe9Ec5eVUIuyGPlG.QX3QDO0wSN0kjNzEzW}`


```bash
/challenge/run
ctrl z
/challenge/run
bg 
pwn.college{AlYp7b8sHukKe9Ec5eVUIuyGPlG.QX3QDO0wSN0kjNzEzW}
```

### New Learnings
using bg command we can resume a suspended process in the background of the terminal. 

### References 
Challenge Description



## Foregrounding Processes
run /challenge/run and suspend it and then resume it in the background of the terminal and then foreground it

### Solve
**Flag:** `pwn.college{gb4W5ATtw6HD3hwAjNLyQmlggBM.QX4QDO0wSN0kjNzEzW}`


```bash
/challenge/run
ctrl z
/challenge/run
bg
fg
pwn.college{gb4W5ATtw6HD3hwAjNLyQmlggBM.QX4QDO0wSN0kjNzEzW}
```

### New Learnings
using fg we resumed a background process

### References 
Challenge Description


## Starting BAckground Processes
In this challenge we are supposed to run /challenge/run without suspending.

### Solve
**Flag:** `pwn.college{0f0WyyOxF5zbyQRjcXSp9PDnNnR.QX5QDO0wSN0kjNzEzW}`


```bash
/challenge/run & bg
pwn.college{0f0WyyOxF5zbyQRjcXSp9PDnNnR.QX5QDO0wSN0kjNzEzW}
```

### New Learnings
using & bg command we directly ran the process in the background

### References 
Challenge Description






## Process Exit Code
In this challenge we should run challenge/get-code to get an error code and give it as argument to /challenge/submit-code to get the flag

### Solve
**Flag:** `pwn.college{ILk9BWkyheZ2ZXtuKFYck4_JbFf.QX5YDO1wSN0kjNzEzW}`


```bash
/challenge/get-code $?
echo $?
/challenge/submit-code 76
pwn.college{ILk9BWkyheZ2ZXtuKFYck4_JbFf.QX5YDO1wSN0kjNzEzW}
```

### New Learnings
 using echo $? commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.
$? is a pre-defined shell variable that holds the error code of the recently executed command

### References 
Challenge Description
