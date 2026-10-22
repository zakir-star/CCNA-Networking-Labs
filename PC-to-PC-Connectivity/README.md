# 🖥️ LAB: PC-to-PC Connectivity Using Static IP Addresses

## 🎯 Objective

- Connect two PCs to a switch and build a basic network.
- Configure static IP addresses on PC1 and PC2.
- Verify connectivity between the PCs using the `ping` command.
- Understand basic IPv4 addressing and subnet masks.

## 🖼️ Lab Topology

![Topology](https://github.com/zakir-star/CCNA-Networking-Labs/blob/main/PC-to-PC-Connectivity/PC-to-PC-Connectivity.png?raw=true)

## 📋 Device Interface Table

| Device | Interface | Connected To | Notes |
|--------|-----------|--------------|-------|
| SW1 | Fa0/1 | PC1 (FastEthernet0) | Copper straight-through cable |
| SW1 | Fa0/2 | PC2 (FastEthernet0) | Copper straight-through cable |

## ⚙️ Configuration

### PC1 Configuration

**Configure the static IP address**

Open PC1 → Desktop → IP Configuration.

Select **Static** and enter the following details:

| Setting | Value |
|---------|-------|
| IPv4 Address | `192.168.1.10` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | Leave blank |
| DNS Server | Leave blank |

### PC2 Configuration

**Configure the static IP address**

Open PC2 → Desktop → IP Configuration.

Select **Static** and enter the following details:

| Setting | Value |
|---------|-------|
| IPv4 Address | `192.168.1.20` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | Leave blank |
| DNS Server | Leave blank |

## ✅ Verification

**Test connectivity from PC1 to PC2**

Open PC1 → Desktop → Command Prompt.

```text
ping 192.168.1.20
```

**Test connectivity from PC2 to PC1**

Open PC2 → Desktop → Command Prompt.

```text
ping 192.168.1.10
```

Both PCs should receive successful ping replies from each other.

## 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| Ping request timed out | Verify the IP addresses, subnet masks, and cable connections |
| Destination host unreachable | Check that both PCs are connected to SW1 and configured in the same subnet |
| Incorrect IP configuration | Recheck the settings under Desktop > IP Configuration |
| First ping fails | Wait for the network to initialize and try the ping command again |

## 🌍 Real-World Use Case

- Static IP addressing is used when devices need predictable IP addresses.
- Devices in the same subnet can communicate directly without requiring a router.
- Network administrators use ping to test connectivity between devices.

## 📌 Outcome

- Static IP addresses configured on PC1 and PC2.
- Both PCs connected to SW1.
- Connectivity verified between the PCs using the `ping` command.

## 🙏 Acknowledgment

- This lab is part of my CCNA practice series. Thank you for taking the time to go through it.

## ✍️ Author's Note

- Prepared and documented by **Zakir Hussain** for CCNA lab practice and GitHub repository organization.

## ✅ Closing

- Thank you for reviewing this lab. Hands-on practice is the best way to learn networking.
