# Level 7

## Objectives

1. SSH to new user `bandit6`
2. Read password from file on the server that has the following properties:
    * owned by user bandit7
    * owned by group bandit6
    * 33 bites in size

### Objective 1

* Username: `bandit6`
* Password: `DXjZPULLxYr17uwoI01bNLQbtFemEgo7`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit6@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Going to have to use find again.

> Find a `file` starting at the root of the file system `/` with a size of `33c` that's owned by the user `bandit7` and the group `bandit6`, then run `stat` on the output.  Send any errors to `/dev/null`.

```sh
bandit6@bandit:~$ find / -type f -size 33c -user bandit7 -group bandit6 -exec stat {} \; 2>/dev/null
  File: /var/lib/dpkg/info/bandit7.password
  Size: 33        	Blocks: 8          IO Block: 4096   regular file
Device: fb01h/64257d	Inode: 920110      Links: 1
Access: (0640/-rw-r-----)  Uid: (11007/ bandit7)   Gid: (11006/ bandit6)
Access: 2020-03-23 07:13:35.449665626 +0100
Modify: 2018-10-16 14:00:51.370867000 +0200
Change: 2018-10-16 14:00:51.370867000 +0200
 Birth: -
```

```sh
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```