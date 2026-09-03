## IT-PC1 ip address config
```
sudo ip addr add 192.168.10.10/24 dev eth0 
#check eth0 network interface is there or use ens2 to check use 
ip addr
```
### set a default gateway 
```
sudo ip route add default via 192.168.10.1
```
## IT-PC2 ip address & defult gateway
```
sudo ip addr add 192.168.10.11/24 dev ens2
sudo ip route add default via 192.168.10.1
ping -c 4 192.168.10.1 # check the ping connection 
ping -c 4 192.168.10.10 # ping both the pc
```
