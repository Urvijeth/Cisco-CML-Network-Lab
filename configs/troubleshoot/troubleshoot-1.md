## Troubleshooting - 1

### HR-PC1

The HR-PC1 was unable to ping its default gateway. The following command resulted in **100% packet loss**:

```bash
ping -c 4 192.168.20.1
```

### Checking VLAN 20 on the Core Switch

First, verify that VLAN 20 is active and that its SVI is up on the Core Switch.

```cisco
show ip interface brief
```

![Core Switch VLAN 20 Status](../img/truble-shoot-core.jpg)

The Core Switch configuration was correct, and **VLAN 20 was in an up/up state**.

The ping was tested again:

```bash
ping -c 4 192.168.20.1
```

However, the connectivity issue still remained.

### Checking the Trunk Configuration

Next, the trunk configuration on the IOSV-HR-SW was checked:

```cisco
show interfaces trunk
```

The **Gi0/0 interface on IOSV-HR-SW was correctly trunking**, and **VLAN 20 was allowed and forwarding** across the trunk.

### Checking the Core Switch Port

The Core Switch port connected to the HR switch was then inspected:

```cisco
show interfaces gigabitEthernet 0/2 switchport
```

![Core Gi0/2 Switchport Status](../img/truble-shoot-core.jpg)

### Problem Identified

The problem was found on **Core Switch Gi0/2**.

The interface was configured as a **static access port in VLAN 20** instead of a trunk port. Because the connection between the Core Switch and HR Switch requires VLAN trunking, VLAN 20 traffic was not being carried correctly.

### Fix: Change the Port from Access to Trunk

Configure Gi0/2 as a trunk port:

```cisco
enable
configure terminal

interface gigabitEthernet 0/2

switchport trunk encapsulation dot1q
switchport mode trunk

no shutdown

end
```

### Verification

After applying the configuration, verify that Gi0/2 is operating as a trunk:

```cisco
show interfaces trunk
```

Then test connectivity from HR-PC1 again:

```bash
ping -c 4 192.168.20.1
```

The issue was resolved by changing **Core Gi0/2 from an access port to a trunk port**, allowing VLAN 20 traffic to pass correctly between the Core Switch and IOSV-HR-SW.