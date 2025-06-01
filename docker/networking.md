```bash
# show IP address
ip a show

# docker interface is docker0

# check bridge link installation
ls /usr/sbin/bridge

# export bridge
export PATH=$PATH:/usr/sbin

# check bridge link to docker0
bridge link

# list network
docker network ls

# inspect bridge
docker inspect bridge

# check ip route
ip route

# create your own docker network
docker network create <NETWORK_NAME>

# create a container in your own network
docker run -itd --rm --network <NETWORK_NAME> --name <CONTAINER_NAME> <CONTAINER>
# EX: docker run -itd --rm --network my-network --name kale busybox

# create ipvlan network; use `ip route` to find subnet and router ip as gateway
docker network create -d ipvlan \
    --subnet <SUBNET_IP> \
    --gateway <GATEWAY_IP> \
    -o parent=<ROUTER_INTERFACE> \
    new-network

# run docker container with macvlan network
docker run -itd --rm --network new-network \
    --ip <IP_V4> \
    --name thor busybox
```