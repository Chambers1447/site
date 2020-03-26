# Level 20

## Objectives

1. SSH to `bandit19`
2. Use the SUID binary in the homedirectory to get the password from `/etc/bandit_pass`

### Objective 1

* Username: `bandit19`
* Password: `IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit19@bandit.labs.overthewire.org
```

> Success!

### Objective 2

We need to find out how to use the binary.

They tell us to run the binary without arguments to learn what it does.

```sh
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id
```

So all we need to do is run the binary (which should run as `bandit20`) to try to read `/etc/bandit_pass/bandit20`.

```sh
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```