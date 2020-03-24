# Level 31

## Objectives

1. SSH to `bandit30`
2. Clone the repo

### Objective 1

* Username: `bandit30`
* Password: `5b90576bedb2cc04c86a9e924ce42faf`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit30@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Create a working directory in `/tmp`.

Clone the `ssh://bandit30-git@localhost/home/bandit30-git/repo` repo they give us and use the same password.

```sh
bandit30@bandit:/tmp/dirwalk$ git clone ssh://bandit30-git@localhost/home/bandit30-git/repo
bandit30@bandit:/tmp/dirwalk$ ls repo/
README.md
bandit30@bandit:/tmp/dirwalk$ cat repo/README.md 
just an epmty file... muahaha
```

Not a whole lot there, so let's keep looking.

No extra branches or no extra commits, seems pretty empty.

How about git tags?

```sh
bandit30@bandit:/tmp/dirwalk$ git tag
secret
bandit30@bandit:/tmp/dirwalk$ git show secret
47e603bb428404d265f59c42920d81e5
```