## Table of contents
- install kvm
- install virtualbox

----------------------------------------------------------------------
## Contents

- install kvm
```bash
# install cpu-checker
sudo apt install cpu-checker

# checking whether support or not
kvm-ok

# install dependencies
sudo apt install qemu-kvm virt-manager libvirt-daemon-system virtinst libvirt-clients bridge-utils


# enable kvm
sudo systemctl enable --now libvirtd
sudo systemctl start libvirtd

# check status
sudo systemctl status libvirtd

# add kvm to group user
sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER

# open kvm in search tool
virtual machine manager
```

- install virtualbox
```bash
# install base virtualbox package
sudo apt install virtualbox

# install virtualbox extension
sudo apt install virtualbox-ext-pack

# install virtualbox guest additions ISO
sudo apt install virtualbox-guest-additions-iso
```
