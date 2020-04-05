## Establish the variable

```bash
export ip=192.168.1.100
```

### Discover who else is on the network

```bash
netdiscover
```

### Discover IP Mac and Mac vendors from ARP

```bash
netdiscover -r $ip/24
```
