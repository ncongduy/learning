## Table of content
- block device is a type of file
- NFS
- LVM

--------------------------------

## Content

- block device is a type of file
```bash
# list block device
lsblk

# list block device
ls -l /dev | grep "^b"

# print information
sudo fdisk -l /dev/<name_disk>

# create partition on name_disk
gdisk /dev/<name_disk>
"""
? => help
n => add a new partition
first sector => 2048
last sector => +500M (for example)
HEX => 8300
w => write
"""

# check type of file system
sudo blkid /dev/<name_disk>

# create file systems in linux
mkfs.ext4 /dev/<name_disk>

# mount file systems
mkdir /mnt/ext4
mount /dev/<name_disk> /mnt/ext4

# check mounting
mount | grep /dev/<name_disk>
df -hP | grep /dev/<name_disk>

# make the mount available after system reboot
echo "/dev/<name_disk> /mnt/ext4 ext4 rw 0 0" >> /etc/fstab
```

- NFS
```bash
# export all mount defined in /etc/exports
exportfs -a

# manually export a directory
exportfs -o <client_IP>:/software/repos

# mount NFS directory on local directory
mount <NFS_server_IP>:/software/repos /mnt/software/repos
```

- LVM
```bash
# instal LVM
sudo apt install lvm2

# create a physical volume
pvcreate /dev/<name_disk>

# create a volume group
vgcreate <name_volume_group> /dev/<name_disk>

# see detail physical volume 
pvdisplay

# see detail volume group
vgdisplay

# create a logical volume
lvcreate -L 1G -n <name_lv> <name_volume_group>

# see detail logical volume
lvdisplay

# list physical volume
pvs

# list volume group
vgs

# list the logical volume
lvs

# create filesystem of logical volume
mkfs.ext4 /dev/<name_volume_group>/<name_lv>

# mount logical volume
mount -t ext4 /dev/<name_volume_group>/<name_lv> /mnt/vol1

# resize logical volume
lvresize -L +1G -n /dev/<name_volume_group>/<name_lv>

# resize filesystem
resize2fs /dev/<name_volume_group>/<name_lv>

# check size 
df -hP /mnt/vol1

# summary of LVM
"""
volume group contains many physical volume.
create logical volume from volume group.
mount logical volume directory. 
resize logical volume without unmount.

pv => vg => lv => /mnt/<name_dr>
"""
```
