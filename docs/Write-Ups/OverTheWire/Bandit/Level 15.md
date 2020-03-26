# Level 15

## Objectives

1. SSH to user `bandit14`
2. Obtaining the password by submitting the password for `bandit14` to port 30000 on localhost.

### Objective 1

* Username: `bandit14`
* Password: `sshkey.private`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

Assuming you have the private key with the correct permissions, SSH to `bandit14` using the private key (identity file).

```sh
user@localhost:~$ ssh -p 2220 bandit14@bandit.labs.overthewire.org -i sshkey.private
```

> Success!

### Objective 2

The password file was said to be `/etc/bandit_pass/bandit14`, so we need to get that first.

```sh
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

Now that we have the password for `bandit14`, we need to get the password for `bandit15` by submitting the password to 30000. We can do this with `nc` and pasting in the password after the connection.

```sh
bandit14@bandit:~$ nc localhost 30000
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```