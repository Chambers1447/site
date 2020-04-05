## Establish the variable

```bash
export ip=192.168.1.100
```

### Typical Nmap scan

```bash
nmap -sV -sC -O -oA scan $ip
```

### Nmap stealth scan using SYN

```bash
nmap -sS $ip
```

### Nmap stealth scan using FIN

```bash
nmap -sF $ip
```

### Nmap Banner Grabbing

```bash
nmap -sV -sT $ip
```

### Nmap OS Fingerprinting

```bash
nmap -O $ip
```

### Nmap Regular Scan:

```bash
nmap $ip/24
```

### Enumeration Scan All Ports TCP / UDP and output to a txt file

```bash
nmap -oN scan.txt -v -sU -sS -p- -A -T4 $ip
```

### Nmap output to a file:

```bash
nmap -oN scan.txt -p 1-65535 -sV -sS -A -T4 $ip/24
```

### Quick Scan:

```bash
nmap -T4 -F $ip/24
```

### Quick Scan Plus:

```bash
nmap -sV -T4 -O -F --version-light $ip/24
```

### Quick traceroute

```bash
nmap -sn --traceroute $ip
```

### All TCP and UDP Ports

```bash
nmap -v -sU -sS -p- -A -T4 $ip
```

### Intense Scan:

```bash
nmap -T4 -A -v $ip
```

### Intense Scan Plus UDP

```bash
nmap -sS -sU -T4 -A -v $ip/24
```

### Intense Scan ALL TCP Ports

```bash
nmap -p 1-65535 -T4 -A -v $ip/24
```

### Intense Scan - No Ping

```bash
nmap -T4 -A -v -Pn $ip/24
```

### Ping scan

```bash
nmap -sn $ip/24
```

### Slow Comprehensive Scan

```bash
nmap -sS -sU -T4 -A -v -PE -PP -PS80,443 -PA3389 -PU40125 -PY -g 53 --script "default or (discovery and safe)" $ip/24
```

### Scan with Active connect in order to weed out any spoofed ports designed to troll you

```bash
nmap -p1-65535 -A -T5 -sT $ip
```
