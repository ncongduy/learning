## Table of contents
- kernel
- hardware

----------------------------------------------------------------------
## Contents

- kernel
```bash
# check kernel version
uname -r

# check information of machine
uname -a
```

- hardware
```bash
# print the kernel ring buffer
dmesg

# print usb information
dmesg | grep -i usb

# udev management tool
udevadm info --query=path --name=/dev/sda5
udevadm monitor

# list PCI devices
lspci

# display CPU architecture
lscpu

# list the ranges of available memory
lsmem

# display amount of free and used memory
free -h

# list hardware
lshw
```
