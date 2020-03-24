# Level 6

## Objectives

1. SSH to the user `bandit5`
2. Read the password from a file that is in the `inhere` directory and has the following properties:
  * human-readable
  * 1033 bytes in size
  * not executable

### Objective 1

* Username: `bandit5`
* Password: `koReBOKuIDDepwhWk7jZC0RTdopnAYKh`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit5@bandit.labs.overthewire.org
```

> Success!

### Objective 2

There's a lot of directories here, so it would be best to use `find` to do a recursive search, while also searching for the most stringent property: 1033 bytes in size.

> Search for a `file` within the `inhere` directory with a `size` of 1033c (unit indicating `bytes`)

```sh
bandit5@bandit:~$ find inhere -type f -size 1033c
inhere/maybehere07/.file2
```

```sh
bandit5@bandit:~$ cat inhere/maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```