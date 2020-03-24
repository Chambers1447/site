# Level 12

## Objectives

1. SSH to user `bandit11`
2. Read password from file `data.txt` where all uppercase and lowercase letters have been rotated by 13 positions.

### Objective 1

* Username: `bandit11`
* Password: `IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit11@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Since the file is ASCII, we should be able to read from the file and use `tr` to translate characters based on simple regular expression.

> Read `data.txt` into `tr`, which will translate the typical `A-Z` to start at `N` and wrap all the way around to `M`. Do the same for lowercase.

```sh
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```