# 🖥️ Lab: Access Router CLI Through a Console Cable

## 🎯 Objective

Access router **R1's CLI** from **Laptop1** using a console cable, then configure interface **GigabitEthernet0/0/0** with IPv4 address `192.168.1.1/24` and enable the interface.

## 🧰 Lab Environment

- **Simulator:** Cisco Packet Tracer
- **Router:** R1
- **Switch:** SW1
- **End device:** Laptop1
- **Console connection:** Laptop1 RS-232 port to R1 Console port
- **Ethernet connection:** R1 GigabitEthernet0/0/0 to SW1
- **IPv4 address for R1 G0/0/0:** `192.168.1.1/24`

## 🗺️ Topology

**📸Screenshot**

![topology picture](https://github.com/zakir-star/CCNA-Networking-Labs/blob/main/Access-CLI-Through-Console/Access-CLI-Through-Console.png?raw=true)

Build the topology with **one router (R1), one switch (SW1), and one laptop (Laptop1)**.

- Connect **R1 GigabitEthernet0/0/0** to an Ethernet port on **SW1** using a copper straight-through cable.
- Connect **Laptop1 RS-232** to **R1 Console** using a console cable.
- Do not connect Laptop1 to SW1 with an Ethernet cable for this lab.

## ⚙️ Tasks to Perform

### Step 1 — Add the devices

1. Open Cisco Packet Tracer.
2. Place one router and rename it **R1**.
3. Place one switch and rename it **SW1**.
4. Place one laptop and rename it **Laptop1**.

### Step 2 — Connect the devices

1. Connect **R1 GigabitEthernet0/0/0** to an available Ethernet port on SW1 using a copper straight-through cable.
2. Connect **Laptop1 RS-232** to **R1 Console** using a console cable.

### Step 3 — Open R1's CLI from Laptop1

1. Click **Laptop1**.
2. Open **Desktop** and select **Terminal**.
3. Keep the default serial settings:
   - Bits per second: `9600`
   - Data bits: `8`
   - Parity: `None`
   - Stop bits: `1`
   - Flow control: `None`
4. Click **OK**.
5. Press **Enter** to display the router prompt. If the initial configuration dialog appears, enter `no` and press Enter.

### Step 4 — Configure the router interface

Enter the following commands in R1's CLI:

```text
enable
configure terminal
interface gigabitEthernet 0/0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
end
```

### Step 5 — Verify the configuration

Run:

```text
show ip interface brief
```

Confirm that `GigabitEthernet0/0/0` has IP address `192.168.1.1` and that its status changes to `up` when the Ethernet link to SW1 is active. The protocol should also show `up` when the connected Layer 2 link is operational.

Suggested filenames:

- `Access-CLI-Through-Console.pkt`
- `Access-CLI-Through-Console.png`

## ✅ Expected Result

Laptop1 accesses R1's CLI through the console cable. R1's `GigabitEthernet0/0/0` is configured with `192.168.1.1/24` and enabled with `no shutdown`.

**Note:** The console cable provides local CLI access and does not require an IP address. The `192.168.1.1/24` address is assigned to R1's Ethernet interface connected to SW1.
