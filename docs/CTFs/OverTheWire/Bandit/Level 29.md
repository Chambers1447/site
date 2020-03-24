# Level 29

## Objectives

1. SSH to `bandit28`
2. Clone the repository

### Objective 1

* Username: `bandit28`
* Password: `0ef186ac70e04ea33b4c1853d2526fa2`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit28@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Make another directory in `/tmp` to work in.

We are told that the repository is at `ssh://bandit28-git@localhost/home/bandit28-git/repo` and the password is the same.

```sh
bandit28@bandit:/tmp/dirwalk$ git clone ssh://bandit28-git@localhost/home/bandit28-git/repo
```

In the repo, we see a `README.md` file with no password.  You should start working with git to see whatelse we can see.  The good and bad of git, is that it keeps your previous versions of whatever you commited.

We should check the log of commits.

```sh
bandit28@bandit:/tmp/dirwalk$ git log
commit 073c27c130e6ee407e12faad1dd3848a110c4f95
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 16 14:00:39 2018 +0200

    fix info leak

commit 186a1038cc54d1358d42d468cdc8e3cc28a93fcb
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 16 14:00:39 2018 +0200

    add missing data

commit b67405defc6ef44210c53345fc953e6a21338cc7
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 16 14:00:39 2018 +0200

    initial commit of README.md
```

We now know that something was leaked before. Let's check to see what changed between the two.

```sh
bandit28@bandit:/tmp/dirwalk$ git diff 073c27c130e6ee407e12faad1dd3848a110c4f95 186a1038cc54d1358d42d468cdc8e3cc28a93fcb
diff --git a/README.md b/README.md
index 5c6457b..3f7cee8 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: xxxxxxxxxx
+- password: bbc96594b4e001778eee9975372716b2
```