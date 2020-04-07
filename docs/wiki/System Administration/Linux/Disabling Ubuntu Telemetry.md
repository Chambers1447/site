# Disabling Ubuntu Telemetry

## Remove telemetry packages
```sh
apt purge -y ubuntu-report popularity-contest apport whoopsie
```

## Clean up
```sh
apt autoremove -y
apt-get autoclean
```
