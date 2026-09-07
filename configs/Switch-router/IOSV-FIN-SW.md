### config the FINANCE Switch 
```
enable
configure terminal
vlan 30
name FINANCE
end
```
#### IOSV-FIN-SW, configure Gi0/0 (Finance-SW → Core) as a trunk
```
enable
configure terminal
interface gigabitEthernet 0/0
switchport trunk encapsulation dot1q
switchport mode trunk
no shutdown
end
```
### Info

We use the following command when configuring the trunk interface:

```cisco
switchport trunk encapsulation dot1q
```

**Why do we use `dot1q`?**

802.1Q (also called **dot1q**) is the standard used to identify VLANs on a trunk link.

When multiple VLANs travel through a single physical link, the switch needs a way to identify which VLAN each Ethernet frame belongs to.

For example:

- This frame belongs to **VLAN 10**
- This frame belongs to **VLAN 20**
- This frame belongs to **VLAN 30**

802.1Q adds a **VLAN tag** to the Ethernet frame. The receiving switch uses this tag to determine which VLAN the frame belongs to.

**Why is trunking required?**

A trunk link carries traffic from **multiple VLANs** over a single physical connection.

```text
Trunk Link
    │
    ├── VLAN 10
    ├── VLAN 20
    ├── VLAN 30
    └── VLAN 40
```

The VLAN tag allows the receiving switch to correctly identify and forward traffic to the appropriate VLAN.

> **Note:** On some Cisco switch platforms, the trunk encapsulation is already fixed to 802.1Q, so the `switchport trunk encapsulation dot1q` command may not be available or required. On platforms that support multiple encapsulation types, this command explicitly selects 802.1Q.

### In Simple Terms


**Trunk** = Carries multiple VLANs over one physical link.

**802.1Q (dot1q)** = Adds VLAN tags so the switches can identify those VLANs.

```text
Trunk = Multiple VLANs
802.1Q = VLAN Identification / Tagging
```