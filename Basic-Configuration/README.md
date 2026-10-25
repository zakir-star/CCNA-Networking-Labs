# 🔌 LAB: Basic Configuration

## 🎯 Objective

- Connect two PCs to a switch and build a basic network.
- Change the default hostname of the switch to SW1.
- Secure privileged EXEC mode with an enable password.
- Secure console access with a line console 0 password.
- Verify the configuration and save it.

## 🖼️ Lab Topology

![Topology](https://github.com/zakir-star/CCNA-Networking-Labs/blob/main/Basic-Configuration/SW1.png?raw=true)

[⬇️ Download the Packet Tracer file](https://github.com/zakir-star/CCNA-Networking-Labs/raw/refs/heads/main/Basic-Configuration/Basic-Configuration.pkt)

## 📋 Device Interface Table

| Device | Interface | Connected To | Notes |
|--------|-----------|--------------|-------|
| SW1 | Fa0/1 | PC1 (FastEthernet0) | Copper straight-through cable |
| SW1 | Fa0/2 | PC2 (FastEthernet0) | Copper straight-through cable |

## ⚙️ Configuration

### SW1 Configuration

**Enter privileged EXEC mode and global configuration mode**  
Switch> enable  
Switch# configure terminal  

**Change the hostname**  
Switch(config)# hostname SW1  

**Set the enable password**  
SW1(config)# enable secret Cisco123  

**Set the console line password**  
SW1(config)# line console 0  
SW1(config-line)# password Console123  
SW1(config-line)# login  
SW1(config-line)# exit  

**Save the configuration**  
SW1(config)# end  
SW1# copy running-config startup-config  

## ✅ Verification

**Check the configuration**  
SW1# show running-config  

**Check that the ports are up**  
SW1# show interfaces status  

**Test the console and enable passwords**  
Exit the CLI and log in again. SW1 should ask for the console password.  
Type enable. SW1 should ask for the enable password.  

## 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| Console password is not asked | Make sure the login command is configured under line console 0 |
| Switch ports are not green | Check the cables and wait for the ports to come up |
| Configuration is lost after reload | Save it with copy running-config startup-config |

## 🌍 Real-World Use Case

- Every new switch gets a proper hostname so it can be identified on the network.
- Passwords stop unauthorized users from changing the switch configuration.
- Console security protects the device against physical access.

## 📌 Outcome

- Hostname of the switch changed to SW1.
- Enable password configured for privileged EXEC mode.
- Console line password configured.

## 🙏 Acknowledgment

- This lab is part of my CCNA practice series. Thank you for taking the time to go through it.

## ✍️ Author's Note

- Prepared and documented by **Zakir Hussain** for CCNA lab practice and GitHub repository organization.

## ✅ Closing

- Thank you for reviewing this lab. Hands-on practice is the best way to learn networking.
