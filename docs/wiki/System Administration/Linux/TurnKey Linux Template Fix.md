# Turnkey Linux Template Fix
Making TurnKey LXC containers run as unprivileged

In an effort to heighten security, especially for anything that may
or may not be publicly exposed, you should strive to have your
LXC containers run as unprivileged.

There are known problems with `postfix`.  If you remove the following:

```sh
rm -f /var/spool/postfix/dev/urandom
rm -f /var/spool/postfix/dev/random
```

For instance, in Proxmox, after you have removed these files,
you can backup the container, delete the existing container, 
then redeploy the container from backup as an unprivileged container.

You can also avoid triggering the TurnKey containers setup scripts
and hooks by `chroot`ing into the container through the hypervisor.

For example:

```sh
root@proxmox:~# pct list
VMID       Status     Lock         Name                
100        running                 Example

root@proxmox:~# lxc-attach 100
root@Example:~# 
```