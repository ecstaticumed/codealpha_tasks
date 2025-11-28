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

## How to Use
1. Install Suricata on Kali Linux:
   ```bash
   sudo apt update
   sudo apt install suricata -y
