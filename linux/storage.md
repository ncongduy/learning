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

