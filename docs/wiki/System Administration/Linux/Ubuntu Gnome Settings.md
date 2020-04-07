# Ubuntu Gnome Settings

To make for a cleaner look in Gnome, here are some settings I found to do the trick.

## Permanently hides the Ubuntu dock
```sh
gsettings set org.gnome.shell.extensions.dash-to-dock autohide false
gsettings set org.gnome.shell.extensions.dash-to-dock dock-fixed false
gsettings set org.gnome.shell.extensions.dash-to-dock intellihide false
```

## Hides the desktop icons
```sh
gsettings set org.gnome.shell.extensions.desktop-icons show-home false
gsettings set org.gnome.shell.extensions.desktop-icons show-trash false
```

If those don't work, this is probably what you need:

```sh
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```
