### Find disk

```
lsblk
```

### Partition Setup:

```
sudo parted /dev/sd[x]
mklabel gpt
print
set unit GB
mkpart primary 0 1000
print
quit
```

##### ***OR***

```
parted -a optimal /dev/sd[x] mkpart primary 0% 100%
```

> You may need to delete any current partitions

### Make the filesystem and check

```
mkfs.ext4 /dev/sd[X]1
sudo fdisk -l
```

### Encrypted Disk Setup:

```
sudo fdisk -l
sudo cryptsetup -v -y luksFormat /dev/sd[X]1
sudo cryptsetup luksOpen /dev/sd[X]1 [dev mapper name]
sudo mkfs.ext4 /dev/mapper/[dev mapper name]
mkdir [mount point]
sudo mount /dev/mapper/[dev mapper name] [mount point]
sudo chown -R $USER:$USER [mount point]
```

### Auto Mount Disk:

```
sudo vim /etc/fstab
```

### Add this line

```
/dev/mapper/[dev mapper name] [mount point] ext4 defaults 0 2
```

### Key Unlock:

#### Create the keyfile

```
mkdir [hidden keyfile directory]
dd if=/dev/random bs=32 count=4 of=[hidden keyfile directory]/keyfile
sudo cryptsetup luksAddKey /dev/sd[X]1 [hidden keyfile directory]/keyfile
```
#### Get the disk UUID

```
ls -l /dev/disk/by-uuid/
```

#### Edit the crypttab

```
sudo vim /etc/crypttab
```

#### Add this line

```
[dev mapper name] UUID=[uuid of cryptdevice] [hidden keyfile directory]/keyfile luks
```
