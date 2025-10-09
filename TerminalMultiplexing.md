# Terminal Multiplexing

## Launching Screen
launch screen

### Solve
**Flag** `pwn.college{cqbRU21WmpsOqVhrske9fyNT3_J.0VN4IDOxwSN0kjNzEzW}`

```bash
screen
pwn.college{cqbRU21WmpsOqVhrske9fyNT3_J.0VN4IDOxwSN0kjNzEzW}
```
### New Learnings
learned to launch screen

### Refrences
desrciption of the challenge



## Detaching and Attaching
launch screen detach run/challenge/run reattach screen

### Solve
**Flag** ` pwn.college{wlO9jx3fkAnBLQlRIrumWlu7rT0.0lN4IDOxwSN0kjNzEzW}`

```bash
screen
ctrl a then d
/challenge/run
screen -r
 pwn.college{wlO9jx3fkAnBLQlRIrumWlu7rT0.0lN4IDOxwSN0kjNzEzW}
```
### New Learnings
learned to detach and attach screen

### Refrences
desrciption of the challenge


## Finding Sessions
find the sessions reattach them to find the flag

### Solve
**Flag** `pwn.college{0Db2_-aHOqKYdhDrLzZmC0m0Sn8.01N4IDOxwSN0kjNzEzW}`

```bash
 screen -ls
There are screens on:
        144.session_f3aa1cdda2f09d15    (Detached)
        147.session_d275779227645ab0    (Detached)
        150.session_86edc3d0b2201875    (Detached)
3 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_f3aa1cdda2f09d15
[detached from 144.session_f3aa1cdda2f09d15]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_d275779227645ab0
[screen is terminating]
```
### New Learnings
using screen -ls we can find all the sessions and their status 

### Refrences
desrciption of the challenge



## Switching Windows
find the flag in different windows 

### Solve
**Flag** `pwn.college{cpdEIGUzlbQn5sHJYA1ETj6bp_8.0FO4IDOxwSN0kjNzEzW}`

```bash
 screen -ls
There are screens on:
        144.session_f3aa1cdda2f09d15    (Remote or dead)
        150.session_86edc3d0b2201875    (Remote or dead)
        135.challenge_session   (Detached)
3 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~switching-windows:~$ screen -r challenge_session
[detached from 135.challenge_session]
```
### New Learnings
ctrl A then 0-9 shows all the running windows in a session

### Refrences
desrciption of the challenge



## Detaching and Attaching tmux
Launch tmux
Detach from it.
Run /challenge/run (this will send the flag to your detached session!)
Reattach to see your prize

### Solve
**Flag** ` pwn.college{chSt7GU_toE0v9EixlYTXCoB9xq.0VO4IDOxwSN0kjNzEzW}`

```bash
 tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[exited]
```
### New Learnings
instead of ctrl a we use ctrl b then d to detach and tmux a to attach 

### Refrences
desrciption of the challenge



## Switching windows tmux
switch to windows 0 insude the tmux session to get the flag

### Solve
**Flag** `pwn.college{MNhxLx77iPQWp7JoHwm3oS59b8C.0FM5IDOxwSN0kjNzEzW}`

```bash
 tmux ls
1: 1 windows (created Thu Oct  9 06:24:02 2025)
2: 1 windows (created Thu Oct  9 06:24:42 2025)
challenge_session: 2 windows (created Thu Oct  9 06:23:10 2025)
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux attach -t challenge_session
 Excellent work! You found window 0!
> Here is your flag: pwn.college{MNhxLx77iPQWp7JoHwm3oS59b8C.0FM5IDOxwSN0kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{MNhxLx77iPQWp7JoHwm3oS59b8C.0FM5IDOxwSN0kjNzEzW}
```
### New Learnings
we can switch windowns inside a tmux session using ctrl b 0-9 

### Refrences
desrciption of the challenge
