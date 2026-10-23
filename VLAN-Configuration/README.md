# 🔀 Lab 3: VLAN Configuration

## 🎯 Objective

- Create VLAN 10 named `IT` and VLAN 20 named `HR`.
- Assign switch ports to the correct VLANs.
- Configure IP addresses on PC1 and PC2.
- Verify VLAN membership and understand communication between different VLANs.

## 🖼️ Lab Topology

![VLAN Configuration Topology](https://github.com/zakir-star/CCNA-Networking-Labs/blob/main/VLAN-Configuration/VLAN-Configuration.png?raw=true)

[Download the Packet Tracer file](VLAN-Configuration.pkt)

## 📋 Device Interface Table

| Device | Interface | Connected To | VLAN |
|--------|-----------|--------------|------|
| SW1 | Fa0/1 | PC1 (FastEthernet0) | VLAN 10 — IT |
| SW1 | Fa0/2 | PC2 (FastEthernet0) | VLAN 20 — HR |

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

**Save the configuration**  
Switch(config)# end  
Switch# copy running-config startup-config  

### PC IP Configuration

Configure the following IPv4 addresses under **Desktop → IP Configuration** on each PC.

| Setting | PC1 | PC2 |
|---------|-----|-----|
| IPv4 Address | `192.168.10.10` | `192.168.20.10` |
| Subnet Mask | `255.255.255.0` | `255.255.255.0` |
| Default Gateway | Leave blank | Leave blank |
| DNS Server | Leave blank | Leave blank |

## ✅ Verification

**Verify VLANs and port assignments**  
SW1# show vlan brief  

Expected: VLAN 10 (`IT`) includes Fa0/1, and VLAN 20 (`HR`) includes Fa0/2.

**Test connectivity**

From PC1, open **Desktop → Command Prompt** and run:

ping 192.168.20.10

The ping should fail because PC1 and PC2 are in different VLANs and no router or Layer 3 switch is configured for inter-VLAN routing.

## 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| VLAN does not appear | Check the VLAN creation commands and run `show vlan brief` |
| Port appears in the wrong VLAN | Check the access VLAN assignment on the interface |
| Ping fails between PC1 and PC2 | This is expected in this lab because inter-VLAN routing is not configured |
| PC IP address is incorrect | Recheck the settings under Desktop → IP Configuration |

## 🌍 Real-World Use Case

- VLANs logically separate devices into different broadcast domains.
- Departments such as IT and HR can be placed in separate VLANs.
- Inter-VLAN communication requires a router or Layer 3 switch.

## 📌 Expected Result

- ✅ VLAN 10 (`IT`) and VLAN 20 (`HR`) are created.
- ✅ Fa0/1 is assigned to VLAN 10, and Fa0/2 is assigned to VLAN 20.
- ✅ `show vlan brief` confirms the VLAN membership.
- ✅ PC1 cannot ping PC2 without inter-VLAN routing.

## 🙏 Acknowledgment

This lab is part of my CCNA practice series. Thank you for taking the time to review it.

## ✍️ Author's Note

Prepared and documented by **Zakir Hussain** for CCNA lab practice and GitHub repository organization.

## ✅ Closing

- Thank you for reviewing this lab. Hands-on practice is the best way to learn networking.
