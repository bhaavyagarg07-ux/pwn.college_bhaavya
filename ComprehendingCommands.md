# Comprehending Commands

## cat:not the pet, but the command
reading the flag from the flag file using the cat command

### Solve
**Flag** `pwn.college{EJaUdp9nq7ZkeNQfJQU0s0SKp9f.QXxcTN0wSN0kjNzEzW}`

```bash
cat flag
pwn.college{EJaUdp9nq7ZkeNQfJQU0s0SKp9f.QXxcTN0wSN0kjNzEzW}
```
### New Learnings
learned about cat command which can show us the matter and contents which are written in a file

### Refrences
desrciption of the challenge


## catting absolute paths
reading the flag from the absolute path by using cat command

### Solve
**Flag** `pwn.college{YJnyIJtICwgrkYpnybh4cOLADfb.QX5ETO0wSN0kjNzEzW}`

```bash
cat /flag
pwn.college{YJnyIJtICwgrkYpnybh4cOLADfb.QX5ETO0wSN0kjNzEzW}
```
### New Learnings
learned about cat command that the argument can be a absolute path also

### Refrences
desrciption of the challenge


## more catting practice
cat the flag from some CRAZYYYYYY directory

### Solve
**Flag** `pwn.college{YJnyIJtICwgrkYpnybh4cOLADfb.QX5ETO0wSN0kjNzEzW}`

```bash
cat /usr/include/misc/flag
pwn.college{YJnyIJtICwgrkYpnybh4cOLADfb.QX5ETO0wSN0kjNzEzW}
```
### New Learnings
learned about cat command that the argument can be a CRAZYYYY path also

### Refrences
desrciption of the challenge


## Greppong for a needlwe in a haystack
use the grep command to find the flag in the file which conatins a lot of matter

### Solve
**Flag** `pwn.college{Ysk92zs1J6JIoznBr0nmQQsEq_K.QX3EDO0wSN0kjNzEzW}`

```bash
grep pwn.college /challenge/data.txt
pwn.college{Ysk92zs1J6JIoznBr0nmQQsEq_K.QX3EDO0wSN0kjNzEzW}
```
### New Learnings
when our file contains a lot of matter and we want to find a specific word or phrase where it is contained line using ctrl f in pdf files we can use grep command

### Refrences
desrciption of the challenge


## Comparing files
using the diff command to find difference between the two files and finding the flag

### Solve
**Flag** `pwn.college{YROydbLh54bvpNZebAjQjeAejgd.01MwMDOxwSN0kjNzEzW}`

```bash
diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
pwn.college{YROydbLh54bvpNZebAjQjeAejgd.01MwMDOxwSN0kjNzEzW}
```
### New Learnings
learned about diff command which tells the difference between two files 2c3 in this c means chnges so in file 1 after line 2 and in file 2 after line 3 there was a change in content. 1a2 in this a means add so after line 1 in file 1 add line 2 from file 2.

### Refrences
desrciption of the challenge

## Listing files 
using ls commands to list the files of /challenge and find the name of the file

### Solve
**Flag** `pwn.college{MwUQR6ZMeEcpsL1xyJ4IfPRgoZC.QX4IDO0wSN0kjNzEzW}`

```bash
ls /challenge
30545-renamed-run-7815  DESCRIPTION.md
/challenge/30545-renamed-run-7815
pwn.college{MwUQR6ZMeEcpsL1xyJ4IfPRgoZC.QX4IDO0wSN0kjNzEzW}
```
### New Learnings
learned that using ls command we can list the files present in a directory or any path.

### Refrences
desrciption of the challenge

## Touching Files
use touch command to create two files /tmp/pwn and /tmp/college

### Solve
**Flag** `pwn.college{sOwfNp5WE7aLV4vUr7kTrMnoJd2.QXwMDO0wSN0kjNzEzW}`

```bash
cd /tmp
touch pwn
touch college
/challenge/run
pwn.college{sOwfNp5WE7aLV4vUr7kTrMnoJd2.QXwMDO0wSN0kjNzEzW}
```
### New Learnings
learned that using touch command we can create files in a directory

### Refrences
desrciption of the challenge


## Removing Files
use rm command to delete a file in home directory

### Solve
**Flag** `pwn.college{0rFliMz67m2Mo97Oif8Mzyb76XR.QX2kDM1wSN0kjNzEzW}`

```bash
rm delete_me
/challenge/run
pwn.college{0rFliMz67m2Mo97Oif8Mzyb76XR.QX2kDM1wSN0kjNzEzW}
```
### New Learnings
learned that using rm command we can delete files in a directory

### Refrences
desrciption of the challenge


## Moving Files
use mv command to move a files around

### Solve
**Flag** `pwn.college{ocxHR0igkUqOjZDtrCdW_WEjm24.0VOxEzNxwSN0kjNzEzW}`

```bash
mv /flag /tmp/hack-the-planet
/challenge/run
pwn.college{ocxHR0igkUqOjZDtrCdW_WEjm24.0VOxEzNxwSN0kjNzEzW}
```
### New Learnings
learned that using mv command we can move files

### Refrences
desrciption of the challenge

