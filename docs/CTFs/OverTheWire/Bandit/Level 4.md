# Level 4

## Objectives

1. SSH user `bandit3`
2. Read a password from a hidden file in the `inhere` directory

### Objective 1

* Username: `bandit3`
* Password: `UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit3@bandit.labs.overthewire.org
```

> Success!

### Objective 2

An `ls` of `inhere` shows us nothing. We need to use the `-a` flag to show us the hidden files.

```sh
bandit3@bandit:~$ ls -a inhere/
.  ..  .hidden
```

Now we just need to read from the hidden file.

```sh
bandit3@bandit:~$ cat inhere/.hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```