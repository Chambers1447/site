# Level 9

## Objectives

1. SSH to user `bandit8`
2. Read the password from `file.txt`, which is on the line that only occurs once

### Objective 1

* Username: `bandit8`
* Password: `cvX2JJa4CFALtqS87jk27qwqGhBM9plV`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit8@bandit.labs.overthewire.org
```

> Success!

### Objective 2

You need to `sort` the file so you can organize the file, then all you need to do is pass the `uniq` command to pull out the one that occurs once.

```sh
bandit8@bandit:~$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```