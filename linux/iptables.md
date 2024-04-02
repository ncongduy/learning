## Contents
iptables execute from top to bottom.

```bash
# install iptables
sudo apt install iptables

# list iptables
sudo iptables -L

# optional
"""
-A        => add rule
-p        => protocol
-s        => source
-d        => destination
--dport   => destination port
-j        => action to take
"""

# add INPUT condition
sudo iptables -A INPUT -p tcp -s <IP_address> --dport 22 -j ACCEPT # ssh
sudo iptables -A INPUT -p tcp -s <IP_address> --dport 443 -j ACCEPT # https
sudo iptables -A INPUT -p tcp -s <IP_address> --dport 80 -j ACCEPT # http
sudo iptables -A INPUT -j DROP

# add OUTPUT condition
sudo iptables -A OUTPUT -p tcp -d <IP_address> --dport 5432 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -d <IP_address> --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 443 -j DROP
sudo iptables -A OUTPUT -p tcp --dport 80 -j DROP
sudo iptables -A OUTPUT -j DROP

# insert condition
sudo iptables -I OUTPUT -p tcp -d <IP_address> --dport 443 -j ACCEPT

# delete condition
sudo iptables -D INPUT <number_condition>
sudo iptables -D OUTPUT <number_condition>
```
