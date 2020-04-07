# MATE Config

## Load configuration into the database
```sh
dconf load /org/mate/ < mate.conf
```

## Remove the Dock from the Launcher
```sh
dconf write /net/launchpad/plank/docks/dock1/show-dock-item false
```
