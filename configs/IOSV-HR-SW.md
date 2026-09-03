### config vlan 20 to HR
```
enable
configure terminal
vlan 20
name HR
end
```
### Configure Gi0/0 (the link from HR-SW to the Core) as a trunk.
```
enable
configure terminal
interface gigabitEthernet 0/0
switchport trunk encapsulation dot1q
switchport mode trunk
no shutdown
end
```
#### move to the core switch and config the HR-SW Gi0/0 is connected to Core Gi0/2
```
enable
configure terminal
interface gigabitEthernet 0/2
switchport trunk encapsulation dot1q
switchport mode trunk
no shutdown
end
```
### On IOSV-HR-SW, configure the two HR PC ports for VLAN 20
```
enable
configure terminal
interface gigabitEthernet 0/1
switchport mode access
switchport access vlan 20
no shutdown
end
```
