# Untangling 


## Becoming root with su
login as root user and read the flag file

### Solve
**Flag:** `pwn.college{EUwtTr6ZAuxRo-xINF8RSMKbqZp.QX1UDN1wSN0kjNzEzW}`


```bash
 su
pass
ls
cat not-the-flag
pwn.college{EUwtTr6ZAuxRo-xINF8RSMKbqZp.QX1UDN1wSN0kjNzEzW}
```

### New Learnings
sometimes we need to use root access to administer our computer

### References 
Challenge Description





## Other users with su
login as zardus and run /challenge/run

### Solve
**Flag:** `pwn.college{QjwPqO3vpl3iDoBq1_EvfhDJMHR.QX2UDN1wSN0kjNzEzW}`


```bash
su zardus
pass
/challenge/run
pwn.college{QjwPqO3vpl3iDoBq1_EvfhDJMHR.QX2UDN1wSN0kjNzEzW}
```

### New Learnings
with no argument in su it start with root shell otherwise we can specify the user

### References 
Challenge Description



## Cracking passwords
log in as zardus by finding the uers password and run /challenge/run to get the flag

### Solve
**Flag:** `pwn.college{IFUW_EtYbtUe7OIKCmi8R7WcfVr.QX3UDN1wSN0kjNzEzW}`


```bash
/challenge/shadow-leak
/challenge$ john /challenge/shadow-leak
su zardus
/challenge/run
pwn.college{IFUW_EtYbtUe7OIKCmi8R7WcfVr.QX3UDN1wSN0kjNzEzW}
```

### New Learnings
using ohn the ripper program to crack passwords

### References 
Challenge Description



## Using Sudo
read the flag file with sudo access

### Solve
**Flag:** `pwn.college{kY8rgeHXdWowlaOneoijVr6pwfN.QX4UDN1wSN0kjNzEzW}`

```bash
ls
cat not-the-flag
sudo cat not-the-flag
pwn.college{kY8rgeHXdWowlaOneoijVr6pwfN.QX4UDN1wSN0kjNzEzW}
```

### New Learnings
the sudo command acts like a magic key that unlocks special powers, letting you do important tasks that usually only the superuser can do

### References 
Challenge Description and geeks for geeks explanation
