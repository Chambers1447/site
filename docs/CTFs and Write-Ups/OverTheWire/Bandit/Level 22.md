# Level 22

## Objectives

1. SSH to `bandit21`
2. Find out what the cronjob is doing

### Objective 1

* Username: `bandit21`
* Password: `gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit21@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Now we need to look at the `/etc/cron.d/` directory.

```sh
bandit21@bandit:~$ ls -latr /etc/cron.d/
total 28
-rw-r--r--  1 root root  189 Jan 25  2017 atop
-rw-r--r--  1 root root  102 Oct  7  2017 .placeholder
-rw-r--r--  1 root root  120 Oct 16  2018 cronjob_bandit22
-rw-r--r--  1 root root  122 Oct 16  2018 cronjob_bandit23
-rw-r--r--  1 root root  120 Oct 16  2018 cronjob_bandit24
drwxr-xr-x 88 root root 4096 Aug  3  2019 ..
drwxr-xr-x  2 root root 4096 Dec  4 01:58 .
```

Now let's see what we can see:

```sh
bandit21@bandit:~$ cat /etc/cron.d/*
PATH=/bin:/usr/bin:/sbin:/usr/sbin

# daily restart of atop at midnight
0 0 * * * root if [ -d "/run/systemd/system" ]; then systemctl restart atop; else /usr/share/atop/atop.daily \& ; fi
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

Since our next level is `bandit22`, let's see what `/usr/bin/cronjob_bandit22.sh` does.

```sh
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

Now let's see what's in `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`

```sh
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```