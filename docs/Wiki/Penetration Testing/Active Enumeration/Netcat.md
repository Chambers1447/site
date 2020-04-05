## Establish the variable

```bash
export ip=192.168.1.100
```

### Netcat port Scanning

```bash
nc -nvv -w 1 -z $ip 3388-3390
```
