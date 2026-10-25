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
- Basic IPv4 networking and troubleshooting commands

## 🎯 Learning Goals

- Configure end devices with static IPv4 addresses.
- Perform basic switch configuration.
- Understand VLANs, access ports, and trunk links.
- Verify network behavior using IOS show commands and `ping`.
- Progress toward inter-VLAN routing and broader CCNA topics.

## 👨‍💻 Author

**Zakir Hussain**

[![GitHub](https://img.shields.io/badge/GitHub-zakir--star-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/zakir-star)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/zakir-hussain-18b998196)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:zh24074@gmail.com)
