# 🔀 Lab: VLAN Trunking

## 🎯 Objective

- Create VLAN 10 and VLAN 20 on both switches.
- Assign access ports to the correct VLANs.
- Configure Fa0/3 between SW1 and SW2 as a trunk link.
- Verify that VLAN traffic can cross the trunk.
- Test connectivity between PCs in the same VLAN and confirm that PCs in different VLANs cannot communicate directly without inter-VLAN routing.

## 🖼️ Lab Topology

![VLAN Trunking Topology](VLAN-Trunking.png)

[⬇️ Download the Packet Tracer file](VLAN-Trunking.pkt)

## 📋 Device Interface Table

| Device | Interface | Connected To | VLAN / Mode |
|--------|-----------|--------------|-------------|
| SW1 | Fa0/1 | PC1 (FastEthernet0) | VLAN 10 — Access |
| SW1 | Fa0/2 | PC2 (FastEthernet0) | VLAN 20 — Access |
| SW1 | Fa0/3 | SW2 Fa0/3 | Trunk |
| SW2 | Fa0/1 | PC3 (FastEthernet0) | VLAN 10 — Access |
| SW2 | Fa0/2 | PC4 (FastEthernet0) | VLAN 20 — Access |
| SW2 | Fa0/3 | SW1 Fa0/3 | Trunk |

## 🧭 IP Addressing Table

| PC | VLAN | IPv4 Address | Subnet Mask | Default Gateway |
|----|------|--------------|-------------|-----------------|
| PC1 | VLAN 10 | `192.168.10.2` | `255.255.255.0` | Leave blank |
| PC2 | VLAN 20 | `192.168.20.2` | `255.255.255.0` | Leave blank |
| PC3 | VLAN 10 | `192.168.10.3` | `255.255.255.0` | Leave blank |
| PC4 | VLAN 20 | `192.168.20.3` | `255.255.255.0` | Leave blank |

Configure the addresses under **Desktop → IP Configuration** on each PC. No default gateway is required for this Layer 2 switching lab.

## ⚙️ Configuration

### SW1 Configuration

**Create VLAN 10 and name it IT**

```text
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name IT
Switch(config-vlan)# exit
```

**Create VLAN 20 and name it HR**

```text
Switch(config)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# exit
```

**Configure Fa0/1 as an access port in VLAN 10**

```text
Switch(config)# interface fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit
```

**Configure Fa0/2 as an access port in VLAN 20**

```text
Switch(config)# interface fa0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit
```

**Configure Fa0/3 as a trunk port to SW2**

```text
Switch(config)# interface fa0/3
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit
```

**Save the configuration**

```text
Switch(config)# end
Switch# copy running-config startup-config
```

### SW2 Configuration

Configure the same VLANs on SW2, then assign its access ports and trunk port as shown below.

```text
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name IT
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# exit

Switch(config)# interface fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Switch(config)# interface fa0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit

Switch(config)# interface fa0/3
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit

Switch(config)# end
Switch# copy running-config startup-config
```

## ✅ Verification

**Verify VLAN membership on both switches**

Run on SW1 and SW2:

```text
show vlan brief
```

Expected: VLAN 10 (`IT`) includes Fa0/1, and VLAN 20 (`HR`) includes Fa0/2. The trunk port Fa0/3 normally does not appear as an access port under these VLANs.

**Verify the trunk link**

Run on both switches:

```text
show interfaces trunk
```

Expected: Fa0/3 is shown as a trunk port, and VLANs 10 and 20 are allowed and active on the trunk.

**Test connectivity between PCs in the same VLAN**

From PC1, ping PC3:

```text
ping 192.168.10.3
```

Expected: successful replies because PC1 and PC3 are in VLAN 10 and share the same IP subnet.

From PC2, ping PC4:

```text
ping 192.168.20.3
```

Expected: successful replies because PC2 and PC4 are in VLAN 20 and share the same IP subnet.

**Test connectivity between different VLANs**

From PC1, ping PC2:

```text
ping 192.168.20.2
```

Expected: the ping fails because VLAN 10 and VLAN 20 are separate Layer 2 broadcast domains and no inter-VLAN routing is configured.

## 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| VLAN 10 or VLAN 20 is missing | Create the VLAN on both switches and verify with `show vlan brief` |
| PC is assigned to the wrong VLAN | Check the access VLAN on Fa0/1 or Fa0/2 |
| Trunk does not appear | Check the cable and configure Fa0/3 with `switchport mode trunk` on both switches |
| Same-VLAN ping fails | Verify PC IP addresses, subnet masks, access-port assignments, VLAN existence on both switches, and trunk status |
| Different-VLAN ping fails | This is expected without inter-VLAN routing |

## 🌍 Real-World Use Case

- Trunk links carry traffic for multiple VLANs between switches over one physical connection.
- VLANs can span multiple switches while keeping their Layer 2 broadcast domains logically separated.
- Devices in different VLANs require Layer 3 routing to communicate.

## 📌 Expected Result

- ✅ VLAN 10 (`IT`) and VLAN 20 (`HR`) are created on both switches.
- ✅ Fa0/1 is assigned to VLAN 10 and Fa0/2 is assigned to VLAN 20 on each switch.
- ✅ Fa0/3 is configured as the trunk link between SW1 and SW2.
- ✅ `show interfaces trunk` confirms trunk operation and VLANs 10 and 20 are active.
- ✅ PC1 can ping PC3, and PC2 can ping PC4.
- ✅ PCs in different VLANs cannot communicate directly because inter-VLAN routing is not configured.

## 🙏 Acknowledgment

This lab is part of my CCNA practice series. Thank you for taking the time to review it.

## ✍️ Author's Note

Prepared and documented by **Zakir Hussain** for CCNA lab practice and GitHub repository organization.

## ✅ Closing

- Thank you for reviewing this lab. Hands-on practice is the best way to learn networking.
