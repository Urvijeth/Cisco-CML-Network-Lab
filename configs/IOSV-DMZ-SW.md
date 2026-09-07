### IOSV-DMZ-SW switch config create VLAN
```
enable
configure terminal
vlan 100
name DMZ
end
```
### Configure Gi0/1 → WEB-SERVER
```
enable
configure terminal
interface gigabitEthernet 0/1
switchport mode access
switchport access vlan 100
no shutdown
end
```
### Configure Gi0/2 → DNS-SERVER
```
enable
configure terminal
interface gigabitEthernet 0/2
switchport mode access
switchport access vlan 100
no shutdown
end
```