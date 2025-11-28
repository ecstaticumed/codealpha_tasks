# Suricata IDS Project

## Overview
This project demonstrates setting up a Network-based Intrusion Detection System (NIDS) using Suricata on Kali Linux. It includes custom detection rules, real-time monitoring, and automated response mechanisms.

## Features
- Installation and setup of Suricata on Kali Linux
- Configuration of custom detection rules for ICMP Ping, SSH brute force, and blacklisted IPs
- Real-time monitoring of network traffic alerts
- Optional automatic blocking of attacker IPs via UFW and a bash script

## Project Structure
- `suricata.yaml` - Suricata main configuration file (with updated interface)
- `local.rules` - Custom Suricata rules for threat detection
- `block_ip.sh` - Script to automatically block attacker IPs using UFW
- `README.md` - This documentation file


---

## Prerequisites
- Kali Linux (tested on latest version)
- sudo privileges
- Basic knowledge of Linux terminal commands
- UFW firewall installed and enabled (for automatic blocking script)

---

## Installation & Setup

### 1. Install Suricata
```bash
sudo apt update
sudo apt install suricata -y
```
2. Verify Installation
```
suricata --version
```
3. Identify Network Interface
```
ip a
```
4. Configure Suricata Interface
```
sudo nano /etc/suricata/suricata.yaml

Find the line with interface: eth0 and replace eth0 with your interface name.
Save and exit (CTRL+O, Enter, CTRL+X).
```
5. Add Custom Detection Rules
```
Create or edit the local rules file:

sudo nano /etc/suricata/rules/local.rules

Add your rules like:

alert icmp any any -> any any (msg:"ICMP Ping Detected"; sid:10001; rev:1;)
alert tcp any any -> any 22 (msg:"Possible SSH Brute Force"; threshold:type threshold, track by_src, count 5, seconds 60; sid:10002; rev:1;)
alert ip any any -> 45.67.89.10 any (msg:"Traffic to Blacklisted IP"; sid:10003; rev:1;)

Save and exit.
```
Running Suricata
```
Start Suricata as a Service:
sudo systemctl start suricata
sudo systemctl enable suricata
```
Monitoring Alerts
```
Suricata logs alerts in:
/var/log/suricata/fast.log
```
To monitor live alerts, use:
```
tail -f /var/log/suricata/fast.log
```
When suspicious activity is detected, you will see alerts like:
```
01/21/2025-15:32:12 [**] ICMP Ping Detected [**] [Priority: 3] {ICMP} 192.168.1.5 -> 8.8.8.8
```
```Response Mechanism - Automatic Blocking
```
1. Setup the blocking script
```
Edit or create the script:

sudo nano /usr/local/bin/block_ip.sh

Paste:

#!/bin/bash
IP=$1
ufw deny from $IP


Save and exit.

Make the script executable:

sudo chmod +x /usr/local/bin/block_ip.sh
```
Testing Your Setup
```
From another machine or terminal, run:

ping <your Kali IP>


You should see an alert for ICMP Ping in Suricata logs.

Attempt multiple SSH connection attempts to trigger SSH brute force detection.
```
Troubleshooting
```
No alerts appearing?
Ensure Suricata is running on the correct network interface.

Script not blocking IPs?

Check UFW status:
sudo ufw status
Make sure UFW is active.

Permissions issues with script?
Confirm block_ip.sh is executable (chmod +x).
```

