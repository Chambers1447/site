## Establish the variable

```bash
export ip=192.168.1.100
```

### Netcat Banner Grab

```bash
nc -v $ip 25
```

### Telnet Banner Grab

```bash
telnet $ip 25
```
