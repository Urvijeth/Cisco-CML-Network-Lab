### set up firewall - password Cisco1@3
```
configure terminal
interface gigabitEthernet0/0
nameif dmz
security-level 50
ip address 192.168.100.1 255.255.255.0
no shutdown
end
```
> **Note:** This gives the ASAv interface a name "nameif dmz" security-level 50 This assigns a security trust level to the interface

### 192.168.100.1 will be the DMZ interface IP of your ASAv firewall (G0/0).
```
configure terminal
interface gigabitEthernet0/0
ip address 192.168.100.1 255.255.255.0
no shutdown
end
```
### ASAv inside interface (G0/1) toward the Core route
```
configure terminal
interface gigabitEthernet0/1
nameif inside
security-level 100
ip address 192.168.254.2 255.255.255.252
no shutdown
end
```
### ASAv outside interface G0/2 toward the IOSV-EDGE
```
configure terminal
interface gigabitEthernet0/2
nameif outside
security-level 0
ip address 203.0.113.2 255.255.255.252
no shutdown
end
```
### ASAv firewall, add the default route toward the EDGE
```
configure terminal
route outside 0.0.0.0 0.0.0.0 203.0.113.1
end
```

**The ASAv firewall has its own IP addresses on each interface:**
- G0/0 (DMZ): 192.168.100.1
- G0/1 (Inside): 192.168.254.2
- G0/2 (Outside): 203.0.113.2

### ASAv routing back to the internal VLANs so the firewall knows how to reach IT, HR, Finance, Management, and Server networks
```
configure terminal
route inside 192.168.10.0 255.255.255.0 192.168.254.1
route inside 192.168.20.0 255.255.255.0 192.168.254.1
route inside 192.168.30.0 255.255.255.0 192.168.254.1
route inside 192.168.50.0 255.255.255.0 192.168.254.1
write memory
```

**If the firewall wants to reach the IT network 192.168.10.0/24, send the traffic to the Core switch at 192.168.254.1 through the inside interface**

### configure NAT on the ASAv so internal traffic can go toward the outside.
```
object network INSIDE-NET
subnet 192.168.0.0 255.255.0.0
nat (inside,outside) dynamic interface
```
### rule written on  firewall too Allow the EDGE (203.0.113.1) to send ping/ICMP traffic to the WEB-SERVER (192.168.100.10) through the ASAv.
```
configure terminal
access-list OUTSIDE_IN extended permit icmp host 203.0.113.1 host 192.168.100.10
end
```

