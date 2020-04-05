### Display a pcap file

```bash
tcpdump -r passwordz.pcap
```

### Display ips and filter and sort

```bash
tcpdump -n -r passwordz.pcap | awk -F" " '{print $3}' | sort -u | head
```

### Grab a packet capture on port 80

```bash
tcpdump tcp port 80 -w output.pcap -i eth0
```

### Check for ACK or PSH flag set in a TCP packet

```bash
tcpdump -A -n 'tcp[13] = 24' -r passwordz.pcap
```
