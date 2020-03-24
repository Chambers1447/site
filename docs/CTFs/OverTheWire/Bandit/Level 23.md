# Level 23

## Objectives

1. SSH to `bandit22`
2. Find out what the cronjob is doing

### Objective 1

* Username: `bandit22`
* Password: `Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit22@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Since we saw from the last level what other scripts were running under `/etc/cron.d`, we know that `/usr/bin/cronjob_bandit23.sh` is our next target.

```sh
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

We need to see what `$mytarget` becomes if `$myname` is `bandit23`.

Then we need to read the output of that from `/tmp/`.

```sh
bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
```