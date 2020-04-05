### Deny traffic to ports except for Local Loopback

```bash
iptables -A INPUT -p tcp --destination-port 13327 ! -d $ip -j DROP
iptables -A INPUT -p tcp --destination-port 9991 ! -d $ip -j DROP
```

### Clear ALL IPTables firewall rules

```bash
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X
iptables -t raw -F iptables -t raw -X
```
