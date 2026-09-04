### config the VLAN id 
```
enable
configure terminal
vlan 40
name MANAGEMENT
end
```
### config the trunk Core Gi1/0 ↔ Management-SW Gi0/0
```
enable
configure terminal
interface gigabitEthernet 0/0
switchport trunk encapsulation dot1q
switchport mode trunk
no shutdown
end
```
**next config the core swicth  configure Core Gi1/0**

### IOSV-MGMT-SW, use Gi0/1 → MGMT-PC:
```
enable
configure terminal
interface gigabitEthernet 0/1
switchport mode access
switchport access vlan 40
no shutdown
end
```
### Configure NMS-SERVER on Gi0/2
```
enable
configure terminal
interface gigabitEthernet 0/2
switchport mode access
switchport access vlan 40
no shutdown
end
```
