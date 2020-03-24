# Level 18

## Objectives
1. SSH to `bandit17` using the SSH private key from level 17.
2. Find the difference between `passwords.old` and `passwords.new` resulting in the password from `passwords.new`.

### Objective 1

* Username: `bandit17`
* Password: `ssh-private-key`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit17@bandit.labs.overthewire.org -i bandit17.rsa
```

> Success!

### Objective 2

To find the difference between the files, all we need to use is the `diff` command.

```sh
bandit17@bandit:~$ diff passwords.new passwords.old 
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> hlbSBPAWJmL6WFDb06gpTx1pPButblOA
```

To interpret this, the `diff` command uses `<` and `>` to indicate which file it came from, based on how you ran the command.

For example, the first file, or the file on the left in my command was the `passwords.new` file, so the arrow `<` indicates that the `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` is what changed in that file, while in the `passwords.old`, the `hlbSBPAWJmL6WFDb06gpTx1pPButblOA` changed.

The goal was to find what changed in the passwords.new file, so the password is `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd`.