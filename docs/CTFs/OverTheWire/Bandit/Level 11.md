# Level 11

## Objectives

1. SSH to user `bandit10`
2. Read password from `data.txt`, which is `base64` encoded

### Objective 1

* Username: `bandit10`
* Password: `truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit10@bandit.labs.overthewire.org 
```

> Success!

### Objective 2

`data.txt` is an ASCII file, so all we'll need to do is read the file and decode it with `base64`.

```
bandit10@bandit:~$ cat data.txt | base64 -d
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```