# XFCE Keybinds

## Tile Corner Keybinds
```sh
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>1" --type string --set "tile_up_left_key"
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>2" --type string --set "tile_up_right_key"
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>3" --type string --set "tile_down_left_key"
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>4" --type string --set "tile_down_right_key"
```

## Tile Half Keybinds
```sh
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>Left" --type string --set "tile_left_key"
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>Right" --type string --set "tile_right_key"
```

## Maximize and Hide Windows
```sh
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>Up" --type string --set "maximize_window_key"
xfconf-query --create --channel xfce4-keyboard-shortcuts --property "/xfwm4/custom/>Super>Down" --type string --set "hide_window_key"
```

## Restart to take effect
```sh
xfce4-panel --quit; pkill xfconfd; cp panel.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml; xfce4-panel &
```
