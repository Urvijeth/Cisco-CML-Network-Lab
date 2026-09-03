### Configure HR-PC1.
```
sudo ip addr add 192.168.20.10/24 dev ens2
sudo ip route add default via 192.168.20.1
ping -c 4 192.168.20.1
```
### do the same Configure HR-PC12 and check the connection 