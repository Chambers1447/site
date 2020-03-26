# Level 27

## Objectives

1. SSH into `bandit26`
2. Break out of the current shell

### Objective 1

* Username: `bandit26`
* Password: `ssh-key`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit26@bandit.labs.overthewire.org -i ssh-key
```

> Success!

### Objective 2

We connected but immediately get disconnected.  

From `bandit25`, check the default shell for `bandit26`.

```sh
bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```

Typical GTFOBins with vi/vim is to make your terminal as small as possible, you can then use vim to give you a shell.

```sh
user@localhost:~$ ssh -p 2220 bandit26@bandit.labs.overthewire.org -i ssh-key
[PRESS V]
:set shell=/bin/bash
:shell
```

Now you should have a shell as `bandit26`.

Now we need to find `bandit27`.

```sh
bandit26@bandit:~$ ls
bandit27-do  text.txt
```

Looks like it's another SUID binary to go get the next password.

Here's what the binary tells us:

```sh
bandit26@bandit:~$ ./bandit27-do 
Run a command as another user.
  Example: ./bandit27-do id
```

Should be very similar to how level 20 was.

```sh
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
3ba3118a22e93127a4ed485be72ef5ea
```