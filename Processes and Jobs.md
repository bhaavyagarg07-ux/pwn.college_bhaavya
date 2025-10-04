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
