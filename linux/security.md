## Best practice

- Automatic security update
```bash
sudo apt update
sudo apt dist-upgrade
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

- Create a user instead of using root user
```bash
sudo adduser <USER_NAME>
sudo usermod -aG sudo <USER_NAME>
```

- Login via secret key 
```bash
# On server
mkdir ~/.ssh && sudo chmod 700 ~/.ssh

# On client
ssh-keygen -b 4096
ssh-copy-id <USER_NAME>@<IP_ADDRESS>
```

- Disable login via password
```bash
sudo vi /etc/ssh/sshd_config

# Port 22 (could change another port. It's optional)
# AddressFamily inet (using IPV4 only)
# PermitRootLogin no 
# PasswordAuthentication no

sudo systemctl restart sshd
```

- Install and configure ufw
```bash
sudo apt install ufw
sudo ufw allow in on tailscale0
sudo ufw allow out on tailscale0
sudo ufw allow ssh/tcp
sudo ufw enable
```

- Disable ping via ufw
```bash
sudo vi /etc/ufw/before.rules

# add the code in line 34
-A ufw-before-input -p icmp --icmp-type echo-request-j DROP

sudo ufw reload
```