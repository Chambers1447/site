# Level 16

## Objectives

1. Get password by sending `bandit15` password to port 30001 via SSL encryption.

### Objective 1

We remain on the same box as before (`bandit14`) and connect via SSL encryption to port 30001.  This can be done easily with the `openssl` command.  You then simply paste the previously recieved password to get the password for `bandit16`.

```sh
bandit14@bandit:~$ openssl s_client -connect 127.0.0.1:30001
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
...
    Start Time: 1584985334
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed
```