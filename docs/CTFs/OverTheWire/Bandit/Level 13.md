# Level 13

## Objectives

1. SSH to user `bandit12`
2. Read the password from file `data.txt` which is a hexdump of a file that has been repeatedly compressed.

### Objective 1

* Username: `bandit12`
* Password: `5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`
* Port: `2220`  
* IP/Hostname: `bandit.labs.overthewire.org`

```sh
user@localhost:~$ ssh -p 2220 bandit12@bandit.labs.overthewire.org
```

### Objective 2

OverTheWire suggests we copy the file to /tmp to work.

```sh
bandit12@bandit:~$ mkdir /tmp/dirwalk
bandit12@bandit:~$ cp data.txt /tmp/dirwalk/
bandit12@bandit:~$ cd /tmp/dirwalk
```

We need to revert the hexdump and push the output to a file.

```sh
bandit12@bandit:/tmp/dirwalk$ xxd -r data.txt > data.1
```

You will need use `file` and rename (`mv`) the file appropriately.

* gzip = .gz
* bzip2 = bz2
* tar = .tar

You will need to decompress each file type with the appropraite command.

* gzip = gunzip
* bzip2 = bunzip2
* tar = tar xf

After you have finished with your `file` and your decompress commands, you will finall have your ASCII text.

```sh
bandit12@bandit:/tmp/dirwalk$ cat data8
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```