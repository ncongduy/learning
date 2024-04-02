## Table of contents
- check info
- managing users
- permission files

----------------------------------------------------------------------
## Contents

- check info
```bash
# check group
cat /etc/group

# check passwd
cat /etc/passwd

# check user
id <name>

# check information
id
who
last

# account type
- user account: pauli, ncd
- supper user account: root (UID = 0)
- system account: ssh, mail (UID < 100 or 100 - 500)
- service account: nginx, docker

# switching user
su -c <name>

# check information in sudoers
cat /etc/sudoers

# search user info
grep -i ^ncd /etc/passwd
USERNAME:PASSWORD:UID:GID:GECOS:HOMEDIR:SHELL

grep -i ^ncd /etc/shadow
USERNAME:PASSWORD:LASTCHANGE:MINAGE:MAXAGE:WARN:INACTIVE:EXPDATE

grep -i ^ncd /etc/group
NAME:PASSWORD:GID:MEMBERS
```

- managing users
```bash
# add user
sudo useradd <name>
sudo useradd -u 1009 -g 1009 -d /home/ncd -s /bin/bash ncd
"""
-c => custom comments
-d => custom home directory
-e => expiry date
-g => specific GID
-G => create user with multiple secondary groups
-s => specific login shells
-u => specific UID
"""

# change password
passwd

# delete user
sudo userdel ncd

# create group
groupadd -g 1011 developer

# delete group
groupdel developer
```

- permission files
```bash
"""
4 => read
2 => write
1 => execute
"""
# change mode of file
sudo chmod <owner><group><others> <file_name>
# EX: sudo chmod 755 send-request.sh

# change owner and group of file
sudo chown <owner>:<group> <file_name>
# EX: sudo chown ncd:developer send-request.sh

# change group of file
sudo chgrp <group> <file_name>
```
