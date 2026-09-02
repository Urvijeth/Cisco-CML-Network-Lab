## IOSV2-CORE Switch Configuration

The IOSV2-CORE switch is configured with the required VLANs to provide network segmentation for different departments and network services.

###  Create VLANs

Start the Cisco Core Switch in Cisco Modeling Labs (CML). Right-click the **IOSV2-CORE** device and select **Console**.

Enter privileged EXEC mode and global configuration mode:

```cisco
enable
configure terminal
```

Create the required VLANs:

```cisco
vlan 10
 name IT
 exit

vlan 20
 name HR
 exit

vlan 30
 name FINANCE
 exit

vlan 40
 name MANAGEMENT
 exit

vlan 50
 name SERVER
 exit

vlan 100
 name DMZ
 exit

end
```

### Verify VLAN Configuration

Run the following command to verify that all VLANs have been created successfully:

```cisco
show vlan brief
```

### VLANs Configured

| VLAN ID | VLAN Name | Purpose |
|--------:|-----------|---------|
| 10 | IT | IT Department |
| 20 | HR | HR Department |
| 30 | FINANCE | Finance Department |
| 40 | MANAGEMENT | Network Management |
| 50 | SERVER | Server Network |
| 100 | DMZ | DMZ Network |
```
```
### Verify VLAN Configuration
```
Configure the Core Switch gateway IPs
enable
configure terminal

interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface vlan 20
ip address 192.168.20.1 255.255.255.0
no shutdown
exit

interface vlan 30
ip address 192.168.30.1 255.255.255.0
no shutdown
exit

interface vlan 40
ip address 192.168.40.1 255.255.255.0
no shutdown
exit

interface vlan 50
ip address 192.168.50.1 255.255.255.0
no shutdown
exit

interface vlan 100
ip address 192.168.100.1 255.255.255.0
no shutdown
exit
end 

```
### check the config
```
show ip interface brief
```
![Network Topology](img/vlan-ip-set.jpg)

