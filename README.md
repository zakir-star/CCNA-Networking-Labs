# 🌐 CCNA Networking Labs

A hands-on collection of **Cisco CCNA labs** built with Cisco Packet Tracer. This repository documents networking fundamentals through practical topologies, device configurations, verification steps, and connectivity tests.

The goal is to build networking skills progressively — from basic PC addressing and switch configuration to VLANs, trunking, and inter-VLAN routing.

## 📚 Lab Index

### 🧩 Networking Fundamentals

| Lab | Topics Covered | Status |
|---|---|---|
| [🖥️ PC-to-PC Connectivity](PC-to-PC-Connectivity/README.md) | Static IPv4 addressing, subnet masks, and testing connectivity with `ping` | Completed |
| [🔌 Basic Switch Configuration](Basic-Switch-Configuration/README.md) | Switch hostname, enable password, console access, and basic switch setup | Completed |

### 🔀 VLANs and Switching

| Lab | Topics Covered | Status |
|---|---|---|
| [VLAN Configuration](VLAN-Configuration/README.md) | Create VLAN 10 (IT) and VLAN 20 (HR), assign access ports, and verify VLAN membership | Completed |
| [VLAN Trunking](VLAN-Trunking/README.md) | Configure a trunk between SW1 and SW2 and allow VLANs 10 and 20 across the link | Completed |

### 🚦 Next Lab

**Router on a Stick — Inter-VLAN Routing**

Extend the existing VLAN trunking topology by adding router R1 and configuring router subinterfaces to enable communication between VLAN 10 (IT) and VLAN 20 (HR).

## 🧪 Lab Approach

Each lab is organized to make the practical work easy to follow and reproduce:

- **Objective:** what the lab is designed to demonstrate.
- **Topology:** devices, connections, and interface details where applicable.
- **Configuration:** step-by-step device setup.
- **Verification:** commands and connectivity tests to confirm the result.
- **Screenshots and files:** supporting visuals and Packet Tracer files when provided in the individual lab folder.

## 🛠️ Tools

- Cisco Packet Tracer
- Cisco IOS command-line interface (CLI)

## 🗺️ Complete CCNA Lab Roadmap

The roadmap is organized in phases aligned with the major CCNA learning areas. Completed labs are linked directly; upcoming labs are marked as planned so the repository can grow in a clear, structured order.

### Phase 1 — Network Fundamentals

1. ✅ **PC-to-PC Connectivity** — static IPv4 addressing, subnet masks, and `ping` verification. [Lab README](PC-to-PC-Connectivity/README.md)
2. ✅ **Basic Switch Configuration** — hostname, enable password, and console access. [Lab README](Basic-Switch-Configuration/README.md)
3. 🔜 **IPv4 Addressing and Subnetting** — network IDs, host ranges, broadcast addresses, and subnet calculations. *(Planned)*
4. 🔜 **IPv6 Addressing Basics** — IPv6 address formats, address types, and end-device configuration. *(Planned)*

### Phase 2 — Network Access

5. ✅ **VLAN Configuration** — create VLANs and assign access ports. [Lab README](VLAN-Configuration/README.md)
6. ✅ **VLAN Trunking** — carry multiple VLANs between switches. [Lab README](VLAN-Trunking/README.md)
7. 🔜 **Spanning Tree Protocol (STP)** — observe root bridge selection and loop prevention. *(Planned)*
8. 🔜 **EtherChannel** — bundle switch links and verify the logical port-channel. *(Planned)*
9. 🔜 **Wireless LAN Fundamentals** — wireless components, SSIDs, and basic WLAN configuration concepts. *(Planned)*

### Phase 3 — IP Connectivity

10. 🔜 **Router on a Stick** — configure router subinterfaces for inter-VLAN routing. *(Next lab)*
11. 🔜 **Static Routing** — configure and verify IPv4 static and default routes. *(Planned)*
12. 🔜 **OSPF Single-Area Routing** — configure neighbor relationships and advertise networks. *(Planned)*
13. 🔜 **Routing Table and Path Selection** — inspect route sources and forwarding decisions. *(Planned)*

### Phase 4 — IP Services

14. 🔜 **DHCPv4** — configure address assignment and verify leases. *(Planned)*
15. 🔜 **DNS Fundamentals** — understand name resolution and test client lookups. *(Planned)*
16. 🔜 **NAT and PAT** — translate private addresses and verify translations. *(Planned)*
17. 🔜 **NTP, Syslog, and SNMP Basics** — explore time synchronization, logging, and monitoring. *(Planned)*
18. 🔜 **QoS and File-Transfer Concepts** — study traffic prioritization and TFTP/FTP use cases. *(Planned)*

### Phase 5 — Security Fundamentals

19. 🔜 **Secure Device Management** — passwords, local users, SSH, and secure management access. *(Planned)*
20. 🔜 **Access Control Lists (ACLs)** — filter traffic using standard and extended ACLs. *(Planned)*
21. 🔜 **Switch Port Security** — restrict learned MAC addresses and test violation behavior. *(Planned)*
22. 🔜 **Layer 2 Security** — DHCP snooping, Dynamic ARP Inspection, and related protections. *(Planned)*
23. 🔜 **WLAN Security Basics** — compare wireless authentication and encryption concepts. *(Planned)*

### Phase 6 — Automation and Programmability

24. 🔜 **Network Automation Concepts** — controller-based networking, APIs, and configuration automation concepts. *(Planned)*
25. 🔜 **JSON and REST API Fundamentals** — recognize structured data and basic API request/response patterns. *(Planned)*
26. 🔜 **Configuration Management and Monitoring** — explore how automation can support repeatable network operations. *(Planned)*

> **Roadmap note:** This is a practical learning plan based on the major CCNA topic areas, not a claim that every exam objective is covered by a single lab. Lab status will be updated as each lab is built, tested, and documented.

## 👨‍💻 Author

**Zakir Hussain**

[![GitHub](https://img.shields.io/badge/GitHub-zakir--star-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/zakir-star)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/zakir-hussain-18b998196)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:zh24074@gmail.com)
