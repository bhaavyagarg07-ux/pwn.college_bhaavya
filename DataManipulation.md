# Data Manipulation

## Translating characters
change the case of characters in the flag and display

### Solve
**Flag** `pwn.college{M2HVRgO61QUrBhyu6-jSwKj-Lss.01MxEzNxwSN0kjNzEzW}`

```bash
/challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
pwn.college{M2HVRgO61QUrBhyu6-jSwKj-Lss.01MxEzNxwSN0kjNzEzW}
```
### New Learnings
using tr command we can change output according to our desire

### Refrences
desrciption of the challenge


## Deleting characters
delete ^% from the flag and display

### Solve
**Flag** `pwn.college{gIfpOpQyqHxb2smrA9HqfXNy9rT.0FNxEzNxwSN0kjNzEzW}`

```bash
/challenge/run | tr -d ^%
pwn.college{gIfpOpQyqHxb2smrA9HqfXNy9rT.0FNxEzNxwSN0kjNzEzW}
```
### New Learnings
using tr -d command we can delte characters 

### Refrences
desrciption of the challenge



## Deleting new lines
delete the bunch pf new lines in the flag

### Solve
**Flag** `pwn.college{k0xu9LMsOFZqnazH654NLzT5yf0.0VNxEzNxwSN0kjNzEzW}`

```bash
/challenge/run | tr -d "\n"
pwn.college{k0xu9LMsOFZqnazH654NLzT5yf0.0VNxEzNxwSN0kjNzEzW}
```
### New Learnings
using tr -d "\n" we can delete new lines

### Refrences
desrciption of the challenge


## Extracting the first lines with head
 /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college

### Solve
**Flag** `pwn.college{0TmlKYHzqfAEwi6DSj_OxjEFVQC.0lNxEzNxwSN0kjNzEzW}`

```bash
/challenge/pwn | head -n 7
/challenge/pwn | head -n 7 | /challenge/college
pwn.college{0TmlKYHzqfAEwi6DSj_OxjEFVQC.0lNxEzNxwSN0kjNzEzW}
```
### New Learnings
using head command we can only print the number of lines we want from the output

### Refrences
desrciption of the challenge




## Extracting specific sections of the text
the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line

### Solve
**Flag** `pwn.college{g77g6P6TggLNOdHChUwa01dnhHG.01NxEzNxwSN0kjNzEzW}`

```bash
 /challenge/run
/challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{g77g6P6TggLNOdHChUwa01dnhHG.01NxEzNxwSN0kjNzEzW}
```
### New Learnings
using cut -d " " -f n we can specify the column we want in place of n

### Refrences
desrciption of the challenge


## sorting data
/challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end

### Solve
**Flag** `pwn.college{sUyeVgub68JSyDaBLaGpeXreQIa.0FM0MDOxwSN0kjNzEzW}`

```bash
sort /challenge/flags.txt
pwn.college{sUyeVgub68JSyDaBLaGpeXreQIa.0FM0MDOxwSN0kjNzEzW}

```
### New Learnings
using sort command we can sort the output by default it is alphabettical order -r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order 
we can use these sort -n like this according to our need

### Refrences
desrciption of the challenge

