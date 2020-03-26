# Level 2

## Objectives

1. SSH into the new user
2. Read the password file name `-` in the home directory

### Objective 1

We need to SSH into `bandit1` with the password we just obtained.

* Username: `bandit1`
* Password: `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit1@bandit.labs.overthewire.org
```

> Success!

### Objective 2

An `ls` will show is the file is there.

Doing a `cat -` won't work, as it will be intepreted for flags, so the process will just hang.

A nifty trick to list files in a directory, sort of like `tree` is to do `find .`, which will find all the files in your current directory (`.`).

```sh
bandit1@bandit:~$ find .
.
./.bash_logout
./.profile
./.bashrc
./-
```

Now let's read the file. 

```sh
bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```