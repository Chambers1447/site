# Level 30

## Objectives

1. SSH to `bandit29`
2. Clone the repo

### Objective 1

* Username: `bandit29`
* Password: `bbc96594b4e001778eee9975372716b2`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit29@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Create a working directory in `/tmp`.

Clone the `ssh://bandit29-git@localhost/home/bandit29-git/repo` repo they give us and use the same password.

```sh
bandit29@bandit:/tmp/dirwalk$ git clone ssh://bandit29-git@localhost/home/bandit29-git/repo
```

There's a `README.md` file.  We should read what it has to say.

```sh
bandit29@bandit:/tmp/dirwalk$ cat repo/README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```

To me, this indicates the use of git branches, since that's how you typically separate code in testing vs production.

```sh
bandit29@bandit:/tmp/dirwalk$ git branch -r
  origin/HEAD -> origin/master
  origin/dev
  origin/master
  origin/sploits-dev
bandit29@bandit:/tmp/dirwalk$ git checkout dev
Previous HEAD position was 2af54c5... add some silly exploit, just for shit and giggles
Branch dev set up to track remote branch dev from origin.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/dirwalk$ ls
code  README.md
```

Now we see some stuff. Let's check the `README.md`.

```sh
bandit29@bandit:/tmp/dirwalk$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: 5b90576bedb2cc04c86a9e924ce42faf
```