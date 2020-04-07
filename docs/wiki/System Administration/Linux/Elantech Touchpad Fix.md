# Elantech Touchpad Fix

## Temporary fix:
```sh
sudo sh -c 'echo -n "elantech"> /sys/bus/serio/devices/serio1/protocol'
```

## Permanent fix:

### Edit `/etc/default/grub`
```sh
vim /etc/default/grub
```

### Edit GRUB_CMDLINE_LINUX_DEFAULT with `psmouse.elantech_smbus=0`
```sh
GRUB_CMDLINE_LINUX_DEFAULT=quiet psmouse.elantech_smbus=0
```
> You may have some other arguments in there, like `splash`.

### Update grub to take effect
```sh
update-grub
```

### Reboot
