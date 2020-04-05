### On Server 2 (behind firewall or double NAT):

```
ssh -f -N -T -R<Port opened on Server 1>:0.0.0.0:22 <Server 1 Username>@<Server 1 IP Address>
```

### On Workstation:

```
ssh -f -N -T <Server 1 Username>@<Server 1 IP Address> -M -S <Whatever Control Socket Name> -L <Workstation RHP>:localhost:<Port opened on Server 1>

ssh -p <Workstation RHP> -S <Whatever Control Socket Name> <Server 2 Username>@localhost
```

## Jump Server:

### Remote:

```
ssh -f -N -T -R<Port opening on Jump Server>:0.0.0.0:<Jump server SSH port> <jump username>@<Jump IP address (public IP)>
```

### Jump:

```
ssh -f -N -T -g <jump username>@localhost -L <globally listening port to connect into>:localhost:<port opened initially on jump server>
```

### Host:

```
ssh -p <global listen on jump> <remote username>@<jump server IP address (private IP)>
```
