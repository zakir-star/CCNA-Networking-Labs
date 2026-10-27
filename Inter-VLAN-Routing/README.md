# 🔀 Lab: Inter-VLAN Routing Using a Layer 3 Switch

## 🎯 Objective
- Configure VLAN 10 (`IT`) and VLAN 20 (`HR`) on SW1 and SW2.
- Configure Switch Virtual Interfaces (SVIs) on SW2 to provide the default gateways for both VLANs.
- Enable Layer 3 routing on SW2 and use a routed link between SW2 and R1.
- Configure a default route on SW2, static routes on R1, and Loopback0 (`1.1.1.1/32`) on R1.
- Verify same-VLAN connectivity, inter-VLAN connectivity, and reachability to R1's loopback.

## 🗺️ Lab Topology

![image alt]()

VLAN 10 and VLAN 20 gateways are configured on SW2's SVIs. R1 provides upstream routing and the loopback test destination.

[⬇️ Download the Packet Tracer file](https://github.com/zakir-star/CCNA-Networking-Labs/raw/refs/heads/main/Inter-VLAN-Routing/Inter-VLAN-Routing.pkt)

## 🔌 Device Interface Table

| Device | Interface | Connected To | VLAN / Mode |
|--------|-----------|--------------|-------------|
| SW1 | Fa0/1 | PC1 (FastEthernet0) | VLAN 10 — Access |
| SW1 | Fa0/2 | PC2 (FastEthernet0) | VLAN 20 — Access |
| SW1 | Fa0/3 | SW2 Fa0/3 | Trunk — VLANs 10, 20 |
| SW2 (3560-24PS) | Fa0/1 | PC3 (FastEthernet0) | VLAN 10 — Access |
| SW2 (3560-24PS) | Fa0/2 | PC4 (FastEthernet0) | VLAN 20 — Access |
| SW2 (3560-24PS) | Fa0/3 | SW1 Fa0/3 | Trunk — VLANs 10, 20 |
| SW2 (3560-24PS) | Fa0/4 | R1 G0/0/0 | Routed Layer 3 link |
| SW2 | VLAN 10 | Logical SVI | Gateway: 192.168.10.1/24 |
| SW2 | VLAN 20 | Logical SVI | Gateway: 192.168.20.1/24 |
| R1 | G0/0/0 | SW2 Fa0/4 | Routed Layer 3 link |
| R1 | Loopback0 | Logical interface | 1.1.1.1/32 |

## 🖧 IP Addressing Table

| Device | VLAN / Interface | IPv4 Address | Subnet Mask | Default Gateway / Next Hop |
|--------|------------------|--------------|-------------|-----------------------------|
| PC1 | VLAN 10 — IT | `192.168.10.10` | `255.255.255.0` | `192.168.10.1` |
| PC3 | VLAN 10 — IT | `192.168.10.11` | `255.255.255.0` | `192.168.10.1` |
| PC2 | VLAN 20 — HR | `192.168.20.10` | `255.255.255.0` | `192.168.20.1` |
| PC4 | VLAN 20 — HR | `192.168.20.11` | `255.255.255.0` | `192.168.20.1` |
| SW2 | VLAN 10 SVI | `192.168.10.1` | `255.255.255.0` | — |
| SW2 | VLAN 20 SVI | `192.168.20.1` | `255.255.255.0` | — |
| SW2 | Fa0/4 routed port | `10.0.0.2` | `255.255.255.252` | R1: `10.0.0.1` |
| R1 | G0/0/0 | `10.0.0.1` | `255.255.255.252` | — |
| R1 | Loopback0 | `1.1.1.1` | `255.255.255.255` | — |

## ⚙️ Configuration

### Step 1: Create VLANs on SW1 and SW2

Create VLAN 10 for IT and VLAN 20 for HR on both switches.

On **SW1** and **SW2**, run:

enable  
configure terminal  
vlan 10  
 name IT  
exit  
vlan 20  
 name HR  
end  

Verify:

show vlan brief  

Expected: VLAN 10 (IT) and VLAN 20 (HR) appear on both switches.

### Step 2: Configure PC Access Ports

On **SW1**, assign PC1 to VLAN 10 and PC2 to VLAN 20:

configure terminal  
interface fa0/1  
 switchport mode access  
 switchport access vlan 10  
exit  
interface fa0/2  
 switchport mode access  
 switchport access vlan 20  
end  

On **SW2**, assign PC3 to VLAN 10 and PC4 to VLAN 20:

configure terminal  
interface fa0/1  
 switchport mode access  
 switchport access vlan 10  
exit  
interface fa0/2  
 switchport mode access  
 switchport access vlan 20  
end  

Verify on both switches with `show vlan brief`.

### Step 3: Configure the SW1–SW2 Trunk

Configure Fa0/3 as a trunk on both switches, allowing VLANs 10 and 20.

On **SW1** and **SW2**:

configure terminal  
interface fa0/3  
 switchport mode trunk  
 switchport trunk allowed vlan 10,20  
 no shutdown  
end  

Verify:

show interfaces trunk  

Expected: SW1 Fa0/3 and SW2 Fa0/3 form a trunk carrying VLANs 10 and 20.

### Step 4: Configure the VLAN Gateways on SW2

On the Catalyst 3560-24PS, configure an SVI for each VLAN and enable Layer 3 routing.

configure terminal  
ip routing  
interface vlan 10  
 ip address 192.168.10.1 255.255.255.0  
 no shutdown  
exit  
interface vlan 20  
 ip address 192.168.20.1 255.255.255.0  
 no shutdown  
end  

The SVIs become operational when the VLAN exists and at least one port in that VLAN is active and forwarding.

Verify:

show ip interface brief  
show ip route  

Expected: VLAN 10 and VLAN 20 SVIs have their configured addresses, and SW2 has connected routes for both VLAN subnets when the SVIs are up.

### Step 5: Configure the Routed Link Between SW2 and R1

This connection is **not a trunk**. Convert SW2 Fa0/4 into a Layer 3 routed port and assign the transit IP address.

On **SW2**:

configure terminal  
interface fa0/4  
 no switchport  
 ip address 10.0.0.2 255.255.255.252  
 no shutdown  
end  

On **R1**, configure G0/0/0:

enable  
configure terminal  
interface gigabitEthernet0/0/0  
 ip address 10.0.0.1 255.255.255.252  
 no shutdown  
end  

Verify on both devices:

show ip interface brief  

Expected: SW2 Fa0/4 and R1 G0/0/0 are up/up after the link comes up.

### Step 6: Configure the Default Route on SW2

Point SW2's default route toward R1's transit IP address.

On **SW2**:

configure terminal  
ip route 0.0.0.0 0.0.0.0 10.0.0.1  
end  

Verify:

show ip route  

Expected: SW2 has a static default route using next hop 10.0.0.1.

### Step 7: Configure Loopback0 on R1

On **R1**, create Loopback0 with address 1.1.1.1/32.

configure terminal  
interface loopback0  
 ip address 1.1.1.1 255.255.255.255  
end  

Verify:

show ip interface brief  

Expected: Loopback0 is up/up with IP address 1.1.1.1.

### Step 8: Configure Static Routes on R1

R1 needs routes back to both VLAN subnets through SW2's transit address.

On **R1**:

configure terminal  
ip route 192.168.10.0 255.255.255.0 10.0.0.2  
ip route 192.168.20.0 255.255.255.0 10.0.0.2  
end  

Verify:

show ip route  

Expected: R1 has static routes to 192.168.10.0/24 and 192.168.20.0/24 via 10.0.0.2.

### Step 9: Configure PC IP Addresses and Default Gateways

Open **Desktop → IP Configuration** on each PC and configure:

- PC1 (VLAN 10): IP `192.168.10.10`, mask `255.255.255.0`, gateway `192.168.10.1`.
- PC3 (VLAN 10): IP `192.168.10.11`, mask `255.255.255.0`, gateway `192.168.10.1`.
- PC2 (VLAN 20): IP `192.168.20.10`, mask `255.255.255.0`, gateway `192.168.20.1`.
- PC4 (VLAN 20): IP `192.168.20.11`, mask `255.255.255.0`, gateway `192.168.20.1`.

### Step 10: Verify Connectivity

From PC1, test same-VLAN connectivity to PC3:

ping 192.168.10.11  

From PC2, test same-VLAN connectivity to PC4:

ping 192.168.20.11  

From PC1, test inter-VLAN connectivity to PC2:

ping 192.168.20.10  

From PC4, test inter-VLAN connectivity to PC3:

ping 192.168.10.11  

Finally, from a PC in either VLAN, test reachability to R1's loopback:

ping 1.1.1.1  

Expected: all tests succeed after the VLANs, trunks, SVIs, routed link, and routes are configured correctly.

## 🛠️ Troubleshooting

| Issue | Check |
|-------|-------|
| An SVI is down | Confirm the VLAN exists and at least one access or trunk port in that VLAN is active and forwarding. |
| SW2 Fa0/4 rejects the IP address | Confirm `no switchport` is configured before assigning the Layer 3 IP address. |
| SW2 cannot reach R1 | Check the transit addresses, subnet mask, cable, and interface status on both ends. |
| Same-VLAN ping fails | Check PC addressing, access VLAN assignments, and the SW1–SW2 trunk. |
| Inter-VLAN ping fails | Confirm `ip routing` is enabled on SW2 and both SVIs are up/up; check each PC's default gateway. |
| PC cannot ping 1.1.1.1 | Check SW2's default route, R1's two VLAN static routes, and R1 Loopback0. |

## 🌍 Real-World Use Case

- A multilayer switch can route traffic between VLANs directly using SVIs, without sending each inter-VLAN packet to a router-on-a-stick link.
- A routed switch-to-router link separates internal VLAN routing from upstream routing.
- Static routes provide explicit paths between the router and the VLAN subnets.

## 📌 Expected Result

- ✅ VLAN 10 (IT) and VLAN 20 (HR) are carried across the SW1–SW2 trunk.
- ✅ SW2 SVIs provide gateways `192.168.10.1` and `192.168.20.1`.
- ✅ SW2 routes between VLAN 10 and VLAN 20 with `ip routing` enabled.
- ✅ SW2's default route points to R1 at `10.0.0.1`.
- ✅ R1 Loopback0 responds at `1.1.1.1/32`.
- ✅ R1 has static routes to both VLAN subnets via SW2 at `10.0.0.2`.
- ✅ Same-VLAN, inter-VLAN, and loopback ping tests succeed.

## 🙏 Acknowledgment

This lab demonstrates inter-VLAN routing using a Cisco Catalyst 3560-24PS multilayer switch, SVIs, and static routing in Cisco Packet Tracer. Thank you for taking the time to review it.

## ✍️ Author's Note

Prepared and documented by **Zakir Hussain** for CCNA lab practice and GitHub repository organization.

## ✅ Closing

- Thank you for reviewing this lab. Hands-on practice is the best way to learn networking.
