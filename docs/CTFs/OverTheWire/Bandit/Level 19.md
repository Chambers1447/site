# Level 19

## Objectives

1. SSH to `bandit18`
2. Read the password from file `readme`

### Objective 1

* Username: `bandit18`
* Password: `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit18@bandit.labs.overthewire.org
```

> Successfully connected, but disconnected immediately.

### Objective 2

After we determined that the password was indeed the correct password from the last level, we now need to deal with a `.bashrc` that disconnects us immediately when we connect with SSH.

We know that the file is name `readme` in the home directory, so let's read that file by using SSH to send commands for us.

```
user@localhost:~$ ssh -p 2220 bandit18@bandit.labs.overthewire.org 'cat readme'
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: 
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```