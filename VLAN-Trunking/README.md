# 🔀 Lab: VLAN Trunking

## 🎯 Objective

- Create VLAN 10 named `IT` and VLAN 20 named `HR` on both switches.
- Assign access ports to the correct VLANs.
- Configure Fa0/3 between SW1 and SW2 as a trunk link.
- Allow only VLAN 10 and VLAN 20 on the trunk link on both switches.
- Verify trunk operation and test connectivity between PCs in the same and different VLANs.

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

Switch> enable  
Switch# configure terminal  
Switch(config)# vlan 10  
Switch(config-vlan)# name IT  
Switch(config-vlan)# exit  

**Create VLAN 20 and name it HR**

Switch(config)# vlan 20  
Switch(config-vlan)# name HR  
Switch(config-vlan)# exit  

**Configure Fa0/1 as an access port in VLAN 10**

Switch(config)# interface fa0/1  
Switch(config-if)# switchport mode access  
Switch(config-if)# switchport access vlan 10  
Switch(config-if)# exit  

**Configure Fa0/2 as an access port in VLAN 20**

Switch(config)# interface fa0/2  
Switch(config-if)# switchport mode access  
Switch(config-if)# switchport access vlan 20  
Switch(config-if)# exit  

**Configure Fa0/3 as a trunk port and allow VLANs 10 and 20**

Switch(config)# interface fa0/3  
Switch(config-if)# switchport mode trunk  
Switch(config-if)# switchport trunk allowed vlan 10,20  
Switch(config-if)# exit  

### SW2 Configuration

**Create VLAN 10 and name it IT**

Switch> enable  
Switch# configure terminal  
Switch(config)# vlan 10  
Switch(config-vlan)# name IT  
Switch(config-vlan)# exit  

**Create VLAN 20 and name it HR**

Switch(config)# vlan 20  
Switch(config-vlan)# name HR  
Switch(config-vlan)# exit  

**Configure Fa0/1 as an access port in VLAN 10**

Switch(config)# interface fa0/1  
Switch(config-if)# switchport mode access  
Switch(config-if)# switchport access vlan 10  
Switch(config-if)# exit  

**Configure Fa0/2 as an access port in VLAN 20**

Switch(config)# interface fa0/2  
Switch(config-if)# switchport mode access  
Switch(config-if)# switchport access vlan 20  
Switch(config-if)# exit  

**Configure Fa0/3 as a trunk port and allow VLANs 10 and 20**

Switch(config)# interface fa0/3  
Switch(config-if)# switchport mode trunk  
Switch(config-if)# switchport trunk allowed vlan 10,20  
Switch(config-if)# exit  

## ✅ Verification

**Verify VLAN membership on both switches**

Run on SW1 and SW2:  
show vlan brief  

Expected: VLAN 10 (`IT`) includes Fa0/1, and VLAN 20 (`HR`) includes Fa0/2. The trunk port Fa0/3 normally does not appear as an access port under these VLANs.

**Verify the trunk link and allowed VLANs**

Run on both switches:  
show interfaces trunk  

Expected: Fa0/3 is operating as a trunk, and VLANs 10 and 20 appear in the allowed and active VLAN lists.

**Test connectivity between PCs in the same VLAN**

From PC1, ping PC3:  
ping 192.168.10.3  

Expected: successful replies because both PCs are in VLAN 10 and share the same IP subnet.

From PC2, ping PC4:  
ping 192.168.20.3  

Expected: successful replies because both PCs are in VLAN 20 and share the same IP subnet.

**Test connectivity between different VLANs**

From PC1, ping PC2:  
ping 192.168.20.2  

Expected: the ping fails because VLAN 10 and VLAN 20 are separate Layer 2 broadcast domains and no inter-VLAN routing is configured.

## 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| VLAN 10 or VLAN 20 is missing | Create the VLAN on both switches and verify with `show vlan brief` |
| PC is assigned to the wrong VLAN | Check the access VLAN on Fa0/1 or Fa0/2 |
| Trunk does not appear | Check the cable and configure Fa0/3 as a trunk on both switches |
| VLANs 10 and 20 are not allowed on the trunk | Check `switchport trunk allowed vlan 10,20` on Fa0/3 of both switches |
| Same-VLAN ping fails | Verify PC IP addresses, subnet masks, access-port assignments, VLAN existence on both switches, and trunk status |
| Different-VLAN ping fails | This is expected without inter-VLAN routing |

## 🌍 Real-World Use Case

- Trunk links carry traffic for multiple VLANs between switches over one physical connection.
- VLANs can span multiple switches while keeping their Layer 2 broadcast domains logically separated.
- Restricting allowed VLANs on a trunk limits which VLAN traffic can cross that link.
- Devices in different VLANs require Layer 3 routing to communicate.

## 📌 Expected Result

- ✅ VLAN 10 (`IT`) and VLAN 20 (`HR`) are created on both switches.
- ✅ Fa0/1 is assigned to VLAN 10 and Fa0/2 is assigned to VLAN 20 on each switch.
- ✅ Fa0/3 is configured as the trunk link between SW1 and SW2 on both switches.
- ✅ Only VLANs 10 and 20 are allowed on both trunk interfaces.
- ✅ `show interfaces trunk` confirms trunk operation and the allowed VLAN list.
- ✅ PC1 can ping PC3, and PC2 can ping PC4.
- ✅ PCs in different VLANs cannot communicate directly because inter-VLAN routing is not configured.

## 🙏 Acknowledgment

This lab is part of my CCNA practice series. Thank you for taking the time to review it.

## ✍️ Author's Note

Prepared and documented by **Zakir Hussain** for CCNA lab practice and GitHub repository organization.

## ✅ Closing

- Thank you for reviewing this lab. Hands-on practice is the best way to learn networking.
