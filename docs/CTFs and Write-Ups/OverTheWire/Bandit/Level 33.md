# Level 33

## Objectives

1. SSH to `bandit32`
2. Escape

### Objective 1

* Username: `bandit31`
* Password: `56a9bf19c63d650ce78e6ec0354ee45e`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit32@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Upon connection, it immediately tells us this:

```sh
WELCOME TO THE UPPERCASE SHELL
```

```sh
>> ls
sh: 1: LS: not found
>> LS
sh: 1: LS: not found
>> pwd
sh: 1: PWD: not found
```

Maybe we can use shell variables to replay our command.

```sh
>> pwd
sh: 1: PWD: not found
>> $0
$ ls
uppershell
$ /bin/bash
bandit33@bandit:~$ ls
uppershell
bandit33@bandit:~$ 
```

Now let's just head for the password.

```sh
bandit33@bandit:~$ cat /etc/bandit_pass/bandit33 
c9c3199ddf4121b10cf581a98d51caee
```