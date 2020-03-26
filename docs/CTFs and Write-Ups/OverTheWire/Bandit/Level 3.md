# Level 3

## Objectives

1. SSH to `bandit2`
2. Read a file named `spaces in this filename` in the home directory

### Objective 1

* Username: `bandit2`
* Password: `CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit2@bandit.labs.overthewire.org
```

> Success!

### Objective 2

An `ls` will show us exactly what we expect.

```sh
bandit2@bandit:~$ ls
spaces in this filename
```

We can either handle space with escapes (`\`) or with simple quotes.

```sh
bandit2@bandit:~$ cat 'spaces in this filename'
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

Syntax for escapes would look like this:

```sh
bandit2@bandit:~$ cat spaces\ in\ this\ filename
```