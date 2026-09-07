### set up  IP address 
```
sudo ifconfig eth0 192.168.50.10 netmask 255.255.255.0 up
sudo route add default gw 192.168.50.1
ping -c 4 192.168.50.1
```
### set up the DB-server
```
sudo ifconfig eth0 192.168.50.11 netmask 255.255.255.0 up
sudo route add default gw 192.168.50.1
```
