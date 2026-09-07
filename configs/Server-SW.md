### config the vlan to the server 
```
vlan 50
name SERVER
end
```
### configure the Server-SW → Core link as a trunk.
```
enable
configure terminal
interface gigabitEthernet 0/0
switchport trunk encapsulation dot1q
switchport mode trunk
no shutdown
end
```
### Configure Gi0/1 → FILE-SERVER for VLAN 50
```
enable
configure terminal
interface gigabitEthernet 0/1
switchport mode access
switchport access vlan 50
no shutdown
end
```
### configure Gi0/2 → DB-SERVER for VLAN 50
```
enable
configure terminal
interface gigabitEthernet 0/2
switchport mode access
switchport access vlan 50
no shutdown
end
```