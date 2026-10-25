# 🌐 CCNA Networking Labs

<p align="center">
  <strong>Hands-on Cisco networking labs built with Cisco Packet Tracer</strong><br>
  From network fundamentals to switching, routing, IP services, and network security.
</p>

<p align="center">
  <img alt="Cisco Packet Tracer" src="https://img.shields.io/badge/Platform-Cisco%20Packet%20Tracer-1BA0D7?style=for-the-badge">
  <img alt="Focus" src="https://img.shields.io/badge/Focus-CCNA%20Practical%20Labs-0A66C2?style=for-the-badge">
  <img alt="Status" src="https://img.shields.io/badge/Progress-In%20Development-orange?style=for-the-badge">
</p>

## 👋 About This Repository

Welcome to my **CCNA Networking Labs** repository. This is my hands-on networking portfolio, documenting practical labs with topologies, configurations, verification steps, screenshots, and downloadable Packet Tracer files where available.

The repository follows a progressive learning path: build the fundamentals first, then develop switching and routing skills, and gradually expand into services, security, troubleshooting, and automation.

## 🎯 Career Objective

To strengthen my practical networking knowledge, build a reliable CCNA-level foundation, and document each lab as reproducible technical work.

## 🧠 Technical Skills Roadmap

| Learning Area | Topics |
|---|---|
| **Network Fundamentals** | IPv4/IPv6 addressing, subnetting, end-device configuration, connectivity testing |
| **Network Access** | Switch setup, VLANs, access ports, trunking, STP, EtherChannel, WLAN concepts |
| **IP Connectivity** | Router-on-a-stick, routing tables, static routes, OSPF, path selection |
| **IP Services** | DHCP, DNS, NAT/PAT, NTP, Syslog, SNMP, QoS concepts |
| **Security Fundamentals** | Device hardening, SSH, ACLs, port security, DHCP snooping, Dynamic ARP Inspection |
| **Automation & Programmability** | JSON, REST APIs, controller-based networking, automation concepts |
| **Troubleshooting** | Structured verification using connectivity tests and device show commands |

## 📁 Repository Structure

The learning roadmap is grouped into numbered CCNA topic areas. Existing lab folders are retained in their current locations during this initial makeover so that completed documentation, screenshots, topology images, and Packet Tracer files are not accidentally lost. The module indexes below provide a clear path through the labs.

```text
CCNA-Networking-Labs/
├── 01-Network-Fundamentals/
├── 02-Network-Access/
├── 03-IP-Connectivity/
├── 04-IP-Services/
├── 05-Security-Fundamentals/
├── 06-Automation-and-Programmability/
├── 07-Troubleshooting/
├── 08-Final-Projects/
├── PC-to-PC-Connectivity/          # Existing completed lab
├── Basic-Switch-Configuration/     # Existing completed lab
├── VLAN-Configuration/             # Existing completed lab
├── VLAN-Trunking/                  # Existing completed lab
└── README.md
```

## 🧪 Learning Modules & Lab Progress

### 01 — Network Fundamentals

| Lab | Topics | Status |
|---|---|---|
| [PC-to-PC Connectivity](PC-to-PC-Connectivity/README.md) | Static IPv4 addressing, subnet masks, and `ping` verification | ✅ Completed |
| IPv4 Addressing & Subnetting | Network IDs, usable host ranges, broadcast addresses | 🔜 Planned |
| IPv6 Addressing Basics | IPv6 formats, address types, and client configuration | 🔜 Planned |

### 02 — Network Access

| Lab | Topics | Status |
|---|---|---|
| [Basic Switch Configuration](Basic-Switch-Configuration/README.md) | Hostname, enable password, console access | ✅ Completed |
| [VLAN Configuration](VLAN-Configuration/README.md) | VLAN 10 (IT), VLAN 20 (HR), access-port assignment | ✅ Completed |
| [VLAN Trunking](VLAN-Trunking/README.md) | Trunk between SW1 and SW2; allow VLANs 10 and 20 | ✅ Completed |
| Spanning Tree Protocol (STP) | Root bridge and loop prevention | 🔜 Planned |
| EtherChannel | Link aggregation and port-channel verification | 🔜 Planned |
| Wireless LAN Fundamentals | WLAN components, SSIDs, and basic configuration | 🔜 Planned |

### 03 — IP Connectivity

| Lab | Topics | Status |
|---|---|---|
| **Router on a Stick** | Add R1 to the existing VLAN topology; configure subinterfaces and inter-VLAN routing | 🚧 Next Lab |
| Static Routing | IPv4 static and default routes | 🔜 Planned |
| Single-Area OSPF | Neighbor relationships and route advertisement | 🔜 Planned |
| Routing Table & Path Selection | Route sources and forwarding decisions | 🔜 Planned |

### 04 — IP Services

- 🔜 DHCPv4 and address assignment
- 🔜 DNS fundamentals and name resolution
- 🔜 NAT and PAT
- 🔜 NTP, Syslog, and SNMP
- 🔜 QoS concepts and TFTP/FTP use cases

### 05 — Security Fundamentals

- 🔜 Secure device management with local users and SSH
- 🔜 Standard and extended Access Control Lists (ACLs)
- 🔜 Switch port security
- 🔜 DHCP snooping and Dynamic ARP Inspection
- 🔜 WLAN security fundamentals

### 06 — Automation & Programmability

- 🔜 Controller-based networking and APIs
- 🔜 JSON and REST API fundamentals
- 🔜 Network configuration and monitoring automation concepts

### 07 — Troubleshooting

- 🔜 Layer 1 and Layer 2 connectivity checks
- 🔜 VLAN, trunk, and addressing fault isolation
- 🔜 Routing and gateway troubleshooting
- 🔜 Structured verification with `ping` and IOS `show` commands

### 08 — Final Projects

- 🔜 Integrated switching and routing topology
- 🔜 End-to-end connectivity and verification
- 🔜 Consolidated project documentation

## 🛠️ Tools

- **Cisco Packet Tracer** — building and testing network topologies
- **Cisco IOS CLI** — configuring and verifying network devices
- **GitHub** — version-controlled lab documentation and project files

## 📋 Lab Documentation Standard

Each lab aims to include the relevant items below:

1. **Objective** — what the lab demonstrates.
2. **Topology** — devices, links, and interface details.
3. **Configuration** — clear, reproducible steps.
4. **Verification** — appropriate show commands and connectivity tests.
5. **Evidence and files** — screenshots, topology images, and Packet Tracer downloads when available.

## 📈 Current Progress

- ✅ PC-to-PC Connectivity
- ✅ Basic Switch Configuration
- ✅ VLAN Configuration
- ✅ VLAN Trunking
- 🚧 Router on a Stick — next lab

> **Roadmap note:** This is a practical learning roadmap aligned with major CCNA subject areas. A topic is marked completed only after its lab has been built, tested, and documented.

## 👨‍💻 Author

**Zakir Hussain**

[![GitHub](https://img.shields.io/badge/GitHub-zakir--star-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/zakir-star)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/zakir-hussain-18b998196)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:zh24074@gmail.com)
