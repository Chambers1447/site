# Installing [Code-Server](https://github.com/cdr/code-server) on an LXC Ubuntu 18.04 container

## Introduction

[Code-Server](https://github.com/cdr/code-server) is VS Code running on a remote server, accessible through the browser.

* Code anywhere: Code on your Chromebook, tablet, and laptop with a consistent dev environment. Develop on a Linux machine and pick up from any device with a web browser.

* Server-powered: Take advantage of large cloud servers to speed up tests, compilations, downloads, and more. Preserve battery life when you're on the go since all intensive computation runs on your server.

## Update and upgrade the container

```
apt update && apt upgrade -y
```

## Pull down the latest release of the Code-Server binary

```
cd /tmp
wget https://github.com/cdr/code-server/releases/download/2.1698/code-server2.1698-vsc1.41.1-linux-x86_64.tar.gz
```

## Decompress it

```
tar tvzf code-server2.1698-vsc1.41.1-linux-x86_64.tar.gz
```

## Move the binary to `/usr/bin/`

```
mv code-server2.1698-vsc1.41.1-linux-x86_64/code-server /usr/bin/
```

> This is done to save some time later dealing with paths.  You can use other directories like `/opt`, but to save time in a container `/usr/bin/` will do.

## Test to see if it works

```
code-server --host 0.0.0.0 --port 8080
```

> It will prompt you with a temporary password for now, we will change this later.

You may just be done now, if that's all you want to do.  You'll have a fully functional version of VSCode over the web.  If you would like to add a systemd unit file to start on reboot automatically, that's what we're going to be doing next!

## Creating a user

We should create a user to run this, just so it isn't running as root.  Since VSCode allows you to view system files with it's built in File Explorer, let's try to limit risk by running Code-Server as a less privileged user.

```
useradd -Ums /usr/sbin/nologin code
```

## Creating a startup script

In order to set a password, you need to set the `PASSWORD` environment variable.  An easy, consistent way of handling this is to utilize a bash script.

For example:

```
#!/bin/bash

export PASSWORD=password

code-server --host 0.0.0.0 --port 8080
```

You can test this script and you'll see that now the web server is going to utilize a custom password.

This looks good, but let's add a little more to the script.

Here's how mine looks:

```
#!/bin/bash

export PASSWORD="reallytoughpassword"

code-server --host 0.0.0.0 --port 8080 --disable-telemetry --extensions-dir /home/code/.local/share/code-server/extensions/ --user-data-dir /home/code/.local/share/code-server/User
```

I add in the `--disable-telemetry` to simply disable telemetry for the server.  I also explicitly state the `--extensions-dir` and `--user-data-dir`.  This may not be necessary, but I do so to make sure everything starts appropriately.

I run this script out of the `/opt` folder in to keep things clean and since the systemd unit file will call this file explicitly, I'm not worried about paths.

## SystemD Unit File

Now we need to create a systemd unit file so the server will start when the container starts. My systemd unit file looks like this:

```
[Unit]
Description=Code Service
After=network.target

[Service]
User=code
Group=code
UMask=002

Type=simple
ExecStart=/opt/code.sh
TimeoutStopSec=20
KillMode=process
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Notice the `User=` and `Group=` I have set to the user `code` that I made earlier. I also set the `ExecStart=` to the bash script I created. 

## Enabling and starting the service

```
systemctl enable code.service
systemctl start code.service
```

## Conclusion

Everything should now be up and running. My instance is going to be behind a proxy, so that handles the SSL certificates for me, but you could also add SSL certs to this by adding your cert and key with the respective `--cert` and `--cert-key` flags.

You should now be able to have a consistent dev environment just by using your browser!

For more documentation, head over to the [Code-Server Github page.](https://github.com/cdr/code-server)
