# Level 28

## Objectives

1. SSH to `bandit27`
2. Clone the git repo

### Objective 1

* Username: `bandit27`
* Password: `3ba3118a22e93127a4ed485be72ef5ea`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit27@bandit.labs.overthewire.org
```

> Success!

### Objective 2

We're told to clone a git repository from `ssh://bandit27-git@localhost/home/bandit27-git/repo`.

We need to make a directory in `/tmp` and then clone the repository.

```sh
bandit27@bandit:~$ mkdir /tmp/dirwalk
bandit27@bandit:~$ cd /tmp/dirwalk
bandit27@bandit:/tmp/dirwalk$ git clone ssh://bandit27-git@localhost/home/bandit27-git/repo
```

You should now have a repo.  Inside the repo is `README`, which should contain what we want.

```sh
bandit27@bandit:/tmp/dirwalk$ cat repo/README 
The password to the next level is: 0ef186ac70e04ea33b4c1853d2526fa2
```