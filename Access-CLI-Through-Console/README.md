# 🖥️ Lab: Access CLI Through Console

## 🎯 Objective

- Access router R1's CLI from Laptop1 using a console cable.
- Configure R1's GigabitEthernet0/0/0 interface with IPv4 address `192.168.1.1/24`.
- Enable the interface and verify its status.

## 🧰 Lab Environment

- **Simulator:** Cisco Packet Tracer
- **Router:** R1
- **Switch:** SW1
- **End device:** Laptop1
- **Console cable:** Laptop1 RS-232 to R1 Console
- **Ethernet cable:** R1 GigabitEthernet0/0/0 to SW1

## 🖼️ Lab Topology

![Access CLI Through Console Topology](https://github.com/zakir-star/CCNA-Networking-Labs/blob/main/Access-CLI-Through-Console/Access-CLI-Through-Console.png?raw=true)

[⬇️ Download the Packet Tracer file](https://github.com/zakir-star/CCNA-Networking-Labs/raw/refs/heads/main/Access-CLI-Through-Console/Access-CLI-Through-Console.pkt)

## 📋 Device Interface Table

| Device | Interface | Connected To | Connection Type |
|---|---|---|---|
| Laptop1 | RS-232 | R1 Console | Console cable |
| R1 | Console | Laptop1 RS-232 | Console cable |
| R1 | GigabitEthernet0/0/0 | SW1 Ethernet port | Copper straight-through |
| SW1 | Available Ethernet port | R1 GigabitEthernet0/0/0 | Copper straight-through |

## ⚙️ Tasks to Perform

### Step 1 — Add the devices

1. Open Cisco Packet Tracer.
2. Add one router, one switch, and one laptop.
3. Set the device names to **R1**, **SW1**, and **Laptop1**.

### Step 2 — Connect the devices

1. Connect **R1 GigabitEthernet0/0/0** to an available Ethernet port on SW1 using a copper straight-through cable.
2. Connect **Laptop1 RS-232** to **R1 Console** using a console cable.
3. Do not connect Laptop1 to SW1 using an Ethernet cable.

### Step 3 — Open R1's CLI from Laptop1

1. Click **Laptop1**.
2. Open **Desktop → Terminal**.
3. Keep the default serial settings: **9600 bits per second, 8 data bits, no parity, 1 stop bit, and no flow control**.
4. Click **OK**, then press **Enter**.
5. If the initial configuration dialog appears, enter `no` and press **Enter**.

### Step 4 — Configure R1's interface

Enter the following commands in the Terminal window, one line at a time:

**Enter privileged EXEC mode**  
R1> enable

**Enter global configuration mode**  
R1# configure terminal

**Select GigabitEthernet0/0/0**  
R1(config)# interface gigabitEthernet 0/0/0

**Assign the IPv4 address and subnet mask**  
R1(config-if)# ip address 192.168.1.1 255.255.255.0

**Enable the interface**  
R1(config-if)# no shutdown

**Return to privileged EXEC mode**  
R1(config-if)# end

## ✅ Verification

**Verify the interface address and status**  
R1# show ip interface brief

Expected: GigabitEthernet0/0/0 displays IP address `192.168.1.1`.

The interface and line protocol should show **up/up** when the Ethernet connection to SW1 is operational. If the link is not active yet, check the cable and connected switch port.

## 🛠️ Troubleshooting

| Issue | Fix |
|---|---|
| R1 CLI does not appear | Check that Laptop1 RS-232 is connected to R1 Console, open Desktop → Terminal, and press Enter |
| Terminal displays no response | Confirm the default serial settings are selected |
| Interface IP is incorrect | Re-enter the `ip address 192.168.1.1 255.255.255.0` command under GigabitEthernet0/0/0 |
| Interface is administratively down | Enter `no shutdown` under the interface |
| Interface remains down | Check the Ethernet cable between R1 and SW1 and confirm the switch port is connected |

## 🌍 Real-World Use Case

- A console connection provides local access to configure a router before network management is available.
- An IPv4 address enables the router interface to participate in IP communication on its connected network.
- The `no shutdown` command administratively enables a Cisco IOS interface.

## 📌 Expected Result

- ✅ Laptop1 accesses R1's CLI through the console cable.
- ✅ R1 GigabitEthernet0/0/0 is configured with `192.168.1.1/24`.
- ✅ The interface is enabled with `no shutdown`.
- ✅ `show ip interface brief` displays the configured IP address and interface status.

**Note:** The console cable provides local CLI access and does not require an IP address. The address `192.168.1.1/24` is assigned to R1's Ethernet interface connected to SW1.

## 🙏 Acknowledgment

This lab is part of my CCNA practice series. Thank you for taking the time to review it.

## ✍️ Author's Note

Prepared and documented by **Zakir Hussain** for CCNA lab practice and GitHub repository organization.

## ✅ Closing

- Thank you for reviewing this lab. Hands-on practice is the best way to learn networking.
