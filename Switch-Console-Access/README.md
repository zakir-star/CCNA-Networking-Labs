# 🖥️ Lab: Access a Switch CLI Using a Console Cable

## 🎯 Objective

Connect to a Cisco switch's command-line interface (CLI) locally using a console cable in Cisco Packet Tracer. This lab uses **one switch and one PC**; no Ethernet connection or IP address is required.

## 🧰 Lab Environment

- **Simulator:** Cisco Packet Tracer
- **Network device:** 1 Cisco switch (for example, 2960)
- **End device:** 1 PC
- **Cable:** Console cable (light blue rollover cable)
- **Connection:** PC RS-232 port to switch Console port

## 🗺️ Topology

Place one switch and one PC in the workspace. Connect the PC's **RS-232** port to the switch's **Console** port using the console cable.

> This is a management connection, not an Ethernet link. Do not connect the PC's FastEthernet port for this lab.

**Topology screenshot:** Save a screenshot showing the single PC, single switch, and console cable as `screenshots/console-topology.png` if you maintain a screenshots folder for this lab.

## ⚙️ Steps to Perform

### Step 1 — Add the devices

1. Open Cisco Packet Tracer.
2. Add one Cisco 2960 switch and one PC to the workspace.

### Step 2 — Connect the console cable

1. Select **Connections** (the lightning-bolt icon).
2. Choose the light blue **Console** cable.
3. Click the PC and select **RS-232**.
4. Click the switch and select **Console**.

**Screenshot checkpoint:** Capture the topology after the console cable is connected. Suggested filename: `01-console-cable-connected.png`.

### Step 3 — Open the PC terminal

1. Click the PC.
2. Open the **Desktop** tab.
3. Select **Terminal**.
4. Keep the default serial settings:
   - Bits per second: `9600`
   - Data bits: `8`
   - Parity: `None`
   - Stop bits: `1`
   - Flow control: `None`
5. Click **OK**.

### Step 4 — Access the switch CLI

1. In the terminal window, press **Enter** if the CLI prompt is not displayed.
2. If the initial configuration dialog appears, type `no` and press Enter to continue to the CLI prompt.
3. Confirm that the switch prompt appears, for example:

```text
Switch>
```

**Screenshot checkpoint:** Capture the terminal showing the switch CLI prompt. Suggested filename: `02-switch-cli-access.png`.

### Step 5 — Enter privileged EXEC mode

At the `Switch>` prompt, enter:

```text
enable
```

The prompt should change to:

```text
Switch#
```

You have now accessed privileged EXEC mode through the console connection.

## ✅ Verification

- The PC is connected to the switch's **Console** port using a console cable.
- The terminal displays the switch CLI prompt.
- The `enable` command changes the prompt from `Switch>` to `Switch#`.

No IP addressing, VLAN configuration, or Ethernet link is needed for this lab.

## 📌 Expected Result

Successfully access the Cisco switch CLI locally through the PC's Terminal application and a console cable.

## 📁 Supporting Files

Add the Packet Tracer file and screenshots to this lab folder when available. Suggested filenames:

- `Switch-Console-Access.pkt`
- `screenshots/01-console-cable-connected.png`
- `screenshots/02-switch-cli-access.png`
