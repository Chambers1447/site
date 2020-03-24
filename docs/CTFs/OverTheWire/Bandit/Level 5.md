# Level 5

## Objectives

1. SSH to new user `bandit4`
2. Read the password from the only human-readable file in the `inhere` directory

### Objective 1

* Username: `bandit4`
* Password: `pIwrPrtPN36QITSp3EQaw936yaFoFgAB`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit4@bandit.labs.overthewire.org
```

> Success!

### Objective 2

If you're looking for a "human-readable" file, you're likely looking for an ASCII file. 

Do a file on all of the files in the `inhere` directory.

```sh
bandit4@bandit:~$ file inhere/*
inhere/-file00: data
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data
```

```sh
bandit4@bandit:~$ cat inhere/-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```