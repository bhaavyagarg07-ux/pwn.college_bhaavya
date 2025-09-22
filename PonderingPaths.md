# Pondering Paths

## The root
The biggest box in which the file is saved. it starts with a / absolute path

### Solve
**Flag** `pwn.college{QRSSHQlFU2DpeCvjnLBI4F3aJHU.QX4cTO0wSN0kjNzEzW}`

```bash
/pwn
pwn.college{QRSSHQlFU2DpeCvjnLBI4F3aJHU.QX4cTO0wSN0kjNzEzW}
```
## New Learnings
about the absolute path of a program 

### Refrences
the reference video

## Program and Absolute Paths
We subcategorized the location in root directory there is another challenge directory in which the program run lives.

### Solve
**Flag** `pwn.college{IRgJFGy9lIfxk4aBv-Vq_xyMIn3.QX1QTN0wSN0kjNzEzW}`

```bash
/challenge/run
pwn.college{IRgJFGy9lIfxk4aBv-Vq_xyMIn3.QX1QTN0wSN0kjNzEzW}
```
## New Learnings
about complicated absolute paths that inside the root directory we can make another directory and then another and then accordingly store our progran

## Position thy self
We can look for our files through navigating different directories using cd command (change directory).
we executed the program challenge run through a specific directory

### Solve
**Flag** `pwn.college{IRgJFGy9lIfxk4aBv-Vq_xyMIn3.QX1QTN0wSN0kjNzEzW}`

```bash
cd
cd /usr/share/doc/fontconfig
/challenge/run
pwn.college{IRgJFGy9lIfxk4aBv-Vq_xyMIn3.QX1QTN0wSN0kjNzEzW}
```
## New Learnings
about changing directories and to run a program which is located in a specific directory and to execute the program from a specific path




