# Level 10

## Objectives

1. SSH to user `bandit9`
2. Read the password from `data.txt` from a human-readable string beginning with several `=`.

### Objective 1

* Username: `bandit9`
* Password: `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit9@bandit.labs.overthewire.org
```

> Success!

### Objective 2

A give away from the description is that there are human-readable strings in this file. Typically a `.txt` file is all human-readable. 

Check the file with the `file` command.

```sh
bandit9@bandit:~$ file data.txt 
data.txt: data
```

This isn't a human-readable file, it's a binary.  We can search through binary files with the `strings` command.  It's similar to `cat` in this aspect.

Before we do that, since we know we're looking for "several `=`", we can pipe that into grep with a couple `=`.

```sh
bandit9@bandit:~$ strings data.txt | grep '=='
2========== the
========== password
========== isa
========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```