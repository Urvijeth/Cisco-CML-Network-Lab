## IOSV2-CORE Switch Configuration

The IOSV2-CORE switch is configured with the required VLANs to provide network segmentation for different departments and network services.

### Step 1: Create VLANs

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

### Step 2: Verify VLAN Configuration

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

### Verification Output

The following output confirms that the VLANs were successfully created on the IOSV2-CORE switch.

![VLAN Brief](img/vlan_brief.jpg)