# Level 8

## Objectives

1. SSH to user `bandit7`
2. Find the password in the file `data.txt` next to the word `millionth`

### Objective 1

* Username: `bandit7`
* Password: `HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit7@bandit.labs.overthewire.org
```

> Success!

### Objective 2

All you need to do is `grep` for `millionth`.

```sh
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt 
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```