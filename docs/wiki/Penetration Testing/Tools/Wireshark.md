### Show only SMTP (port 25) and ICMP traffic:

```bash
tcp.port eq 25 or icmp
```
### Show only traffic in the LAN (192.168.x.x), between workstations and servers -- no Internet:

```bash
ip.src==192.168.0.0/16 and ip.dst==192.168.0.0/16
```

### Filter by a protocol ( e.g. SIP ) and filter out unwanted IPs:

```bash
ip.src != xxx.xxx.xxx.xxx && ip.dst != xxx.xxx.xxx.xxx && sip
```

#### Some commands are equal

```bash
ip.addr == xxx.xxx.xxx.xxx
```

#### Equals

```bash
ip.src == xxx.xxx.xxx.xxx or ip.dst == xxx.xxx.xxx.xxx

ip.addr != xxx.xxx.xxx.xxx
```

#### Equals

```bash
ip.src != xxx.xxx.xxx.xxx or ip.dst != xxx.xxx.xxx.xxx
```
