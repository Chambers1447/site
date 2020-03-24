# Level 32

## Objectives

1. SSH to `bandit31`
2. Clone the repo

### Objective 1

* Username: `bandit31`
* Password: `47e603bb428404d265f59c42920d81e5`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit31@bandit.labs.overthewire.org
```

### Objective 2

Create a working directory in `/tmp`.

Clone the `ssh://bandit31-git@localhost/home/bandit31-git/repo` repo they give us and use the same password.

```sh
bandit31@bandit:/tmp/dirwalk$ git clone ssh://bandit31-git@localhost/home/bandit31-git/repo
```

Now let's look around and see what we find.

`README.md` tells us this:

```sh
bandit31@bandit:/tmp/dirwalk$ cat README.md 
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

`.gitignore` tells us this:

```sh
bandit31@bandit:/tmp/dirwalk$ cat .gitignore
*.txt
```

We'll likely need to push `key.txt` to master, keeping mind the `.gitignore`.

```sh
bandit31@bandit:/tmp/dirwalk$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/dirwalk$ git add key.txt -f
bandit31@bandit:/tmp/dirwalk$ git commit -m 'key.txt'
bandit31@bandit:/tmp/dirwalk$ git push origin master
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 319 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: 56a9bf19c63d650ce78e6ec0354ee45e
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
To ssh://localhost/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://bandit31-git@localhost/home/bandit31-git/repo'
```