### Remove telemetry packages

```
apt purge -y ubuntu-report popularity-contest apport whoopsie
```

### Clean up

```
apt autoremove -y
apt-get autoclean
```
