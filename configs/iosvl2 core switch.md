## IOSV2-CORE Switch Configuration

### Step 1: Create VLANs

start the cisco core switch and right click and select consloe 
```cisco
enable
configure terminal

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

### Verify 
show vlan brief

![Vlan brief][img/vlan_brief.jpg]
```

![Vlan brief][img/vlan_brief.jpg]