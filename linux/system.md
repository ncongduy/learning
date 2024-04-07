## Table of contents
- systemd
- journalctl
- file
- compress files
- search files

----------------------------------------------------------------------
## Contents

- systemd
```bash
# check run level
# 5 => GUI; 3 => CLI
runlevel

# get default
systemctl get-default

# set CLI
systemctl set-default multi-user.target
systemctl set-default graphical.target

# creating a systemd service
# /etc/systemd/system/project-name.service
"""
[Unit]
Description=Python Flask app
Documentation=http://wiki.myproject/project-name
After=postgresql.service

[Service]
ExecStart= /bin/bash <path_file>
User=project_name
Restart=on-failure
RestartSec=10

[Install]
WantedBy graphical.target
"""

# start service
systemctl start project-name.service 

# check service
systemctl status project-name.service

# stop service
systemctl stop project-name.service

# detect changes in file `/etc/systemd/system/project-name.service`
systemctl daemon-reload

# systemctl tools
"""
systemctl start docker
systemctl stop docker
systemctl restart docker
systemctl reload docker
systemctl status docker

# persistent across rebot
systemctl enable docker

# disable service
systemctl disable docker

# make systemd aware changes
systemctl daemon-reload

# edit service immediately without running daemon-reload
systemctl edit project-name.service --full

# list all Unit
systemctl list-units --all
"""
```

- journalctl
```
# log from oldest to newest
journalctl

# log current boot
journalctl -b

# log a specific Unit
journalctl -u UNIT
e.g. journalctl -u docker.service
```

- file
```bash
# check file type
file <name_of_file>

# file type and identifier
"""
directory           => d
regular file        => -
character device    => c
link                => l 
socket file         => s
pipe                => p 
block device        => b
"""

# viewing file size
du -sh <file_name>
du -h --max-depth=1 .
```

- compress files
```bash
# archiving files
tar -cf test.tar file1 file2 file3
tar -zcf test.tar file1 file2 file3

# extract files
tar -tf test.tar
tar -xf test.tar

# compressing
bzip2 <file_name> # compress a file from 99M to 4K
gzip <file_name> # compress a file from 99M to 100K
xz <file_name> # compress a file from 99M to 16K

# uncompressing
bunzip2 <file_name>
gunzio <file_name>
unxz <file_name>
```

- search files
```bash
locate <file_name>
# EX: locate city.txt

find <path> -name <file_name>
# EX: find /home/ncd -name city.txt

grep -rin "content" <path>
# EX: grep -rin "abc" .
```
