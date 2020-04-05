### Temporary fix:

```
temp text
```

---

### Grub fix

#### Edit `/etc/default/grub`

```
vim /etc/default/grub
```

#### Edit TEMPMODULELINE with `psmouse.elantech_smbus=0`

```
TEMPMODULELINE=quiet psmouse.elantech_smbus=0
```
#### Update grub to take effect

```
update-grub
```

#### Reboot
