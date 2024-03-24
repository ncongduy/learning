## Table of contents
- how to find IP address
- how to create an user
- how to connect 2 Ubuntu laptops

----------------------------------------------------------------------
## Contents

- how to find IP address
```bash
# solution 1
hostname -I

# solution 2 (find result next to inet)
ifconfig

# solution 3 (find result next to inet)
ip addr show
```

- how to create an user
```bash
# create user
sudo adduser <username>

# Verify user creation
ls /home

# add privilege sudo for user (optional)
sudo usermod -aG sudo <username>

# add privilege docker for user (example) 
sudo usermod -aG docker <username>

# switch user
su - <username>

# change password
passwd

# delete user
sudo userdel <username>
```

- how to connect 2 Ubuntu laptops
```bash
# install openssh for both laptops
sudo apt update
sudo apt install openssh-server

# ssh via password
ssh <username>@<ip_address>

# create ssh key
ssh-keygen -t rsa

# copy ssh key
ssh-copy-id <username>@<ip_address>

# store IP in hosts
sudo nvim /etc/hosts
<name_server> <IP_address>

# ssh after storing IP in hosts
ssh <username>@<name_server>
ssh <name_server>
```
