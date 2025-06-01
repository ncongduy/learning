## Table of contents
- networking basic
- switching & routing
- how to find IP address
- how to create an user
- how to connect 2 Ubuntu laptops
- using scp
- troubleshooting
- tailscale (VPN)

----------------------------------------------------------------------
## Contents

- networking basic
```bash
# use hosts file in /ect/hosts

# use nameserver in /etc/resolv.conf 

# search domain
- ping <url>
- nslookup <url>
- dig <url>

# find public IP address of your machine
curl -s https://ipinfo.io/ip
curl -s https://api.ipify.org
```

- switching & routing
```bash
# show network devices, interfaces
ip link

# show address
ip addr

# connect two machines via switch (interface: eth0)
ip addr add 192.168.1.10/24 dev eth0
ip addr add 192.168.1.11/24 dev eth0

# show IP routing table
route

# show route
ip route

# add route via gateway
ip route add 192.168.2.0/24 via 192.168.1.1
ip route add 192.168.1.0/24 via 192.168.2.1
ip route add default via 192.168.2.1

# check connection by ping from machine (192.168.1.10)
ping 192.168.1.11
```

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

- using scp
```bash
# copy a file from local to server
scp /home/ncd/<file_name> <username>@<name_server>:/home/ncd

# copy directory from local to server
scp -pr /home/ncd/media/ <username>@<name_server>:/home/ncd

# copy from server to local
scp <username>@<name_server>:/home/ncd/<file_name> /home/ncd
```

- troubleshooting
```bash
# check interfaces at local
ip link

# show interface
ip link show <interface>

# check DNS resolution at local
nslookup <DNS server>

# check connectivity at local
ping <name_server>

# check route at local
traceroute <IP_address>

# check service at server - option 1
netstat -an | grep -i LISTEN

# check service at server - option 2
ss -ltn

# start up interface
ip link set dev <interface> up
```

- tailscale
```bash
# Install tailscale on both laptop and desktop
curl -fsSL https://tailscale.com/install.sh | sh

# Login tailscale on both laptop and desktop
sudo tailscale up

# Authenticate on browser

# Get IP of desktop
tailscale ip -4

# ssh to desktop
ssh username@IP
```