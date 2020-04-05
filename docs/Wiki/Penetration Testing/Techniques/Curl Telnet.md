# Curl Telnet

Can be used if you lack `netcat`, `nc`, or `telnet`.

```
echo -e "GET /anything HTTP/1.1\r\nHost: example.com\r\nConnection: close\r\n\r\n" | curl telnet://example.com:80
HTTP/1.1 200 OK
```