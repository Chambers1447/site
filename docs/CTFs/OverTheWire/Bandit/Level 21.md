# Level 21

## Objectives

1. SSH to `bandit20`
2. Use the SUID binary to recieve the password for `bandit21`

### Objective 1

* Username: `bandit20`
* Password: `GbKksEFF4yrVs6il55v6gwY5aVje5f0j`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit20@bandit.labs.overthewire.org
```

> Success!

### Objective 2

Testing the output of the SUID binary in the home directory.

```sh
bandit20@bandit:~$ ./suconnect 
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
```

It appears that we have to control both ends of the connection, so we need to have a `nc` open for the `suconnect` binary to connect and give us the password with.

Connect with another session:

```sh
user@localhost:~$ ssh -p 2220 bandit20@bandit.labs.overthewire.org
```

Now that you're in, you need to start a `nc` server with the password to get the new password.

```sh
bandit20@bandit:~$ echo "GbKksEFF4yrVs6il55v6gwY5aVje5f0j" | nc -nvlp 9001
listening on [any] 9001 ...
```

Now us the SUID binary to make the connection.

```sh
bandit20@bandit:~$ ./suconnect 9001
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```

```sh
bandit20@bandit:~$ echo "GbKksEFF4yrVs6il55v6gwY5aVje5f0j" | nc -nvlp 9001
listening on [any] 9001 ...
connect to [127.0.0.1] from (UNKNOWN) [127.0.0.1] 35764
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```