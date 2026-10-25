# 🖥️ Lab: Access a Switch CLI Through a Console Cable

## 🎯 Objective

Use a laptop and a console cable in Cisco Packet Tracer to access the CLI of a Cisco switch through the laptop's Terminal application.

## 🧰 Lab Environment

- **Simulator:** Cisco Packet Tracer
- **Network device:** 1 Cisco 2960 switch
- **End device:** 1 laptop
- **Cable:** Console cable
- **Connection:** Laptop `RS-232` port to switch `Console` port

## 🗺️ Topology

This lab contains **one switch and one laptop only**. The laptop connects directly to the switch's Console port using a console cable. There are no PCs, routers, or Ethernet connections in this topology.

## ⚙️ Steps to Perform

### Step 1 — Add one switch and one laptop

1. Open Cisco Packet Tracer.
2. Add one Cisco 2960 switch and one laptop to the workspace.

### Step 2 — Connect the console cable

1. Select **Connections** (the lightning-bolt icon).
2. Choose the **Console** cable.
3. Click the laptop and select **RS-232**.
4. Click the switch and select **Console**.

### Step 3 — Open Terminal on the laptop

1. Click the laptop.
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

1. Press **Enter** in the Terminal window if the prompt does not appear.
2. If the initial configuration dialog appears, enter `no` and press Enter.
3. Confirm that the switch prompt appears:

```text
Switch>
```

### Step 5 — Enter privileged EXEC mode

At the `Switch>` prompt, enter:

```text
enable
```

The prompt should change to:

```text
Switch#
```

## ✅ Verification

- The Packet Tracer workspace contains one laptop and one switch.
- The laptop's `RS-232` port is connected to the switch's `Console` port with a console cable.
- The laptop's Terminal displays the switch CLI prompt.
- Entering `enable` changes the prompt from `Switch>` to `Switch#`.

No IP addressing or Ethernet connection is required. The console cable provides local management access to the switch.

## 📌 Expected Result

Successfully access the switch CLI from the laptop's Terminal using a console cable.

## 📁 Lab Files

The Packet Tracer project and its matching topology screenshot will be linked here:

- [Download the Packet Tracer file](Switch-Console-Access.pkt)
- [View the Packet Tracer topology image](Switch-Console-Access.png)

**File note:** Upload the `.pkt` and `.png` files to this folder using these exact filenames so the links work.
