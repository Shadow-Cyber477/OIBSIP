# Basic Firewall Configuration with UFW

## Overview
This repository contains the setup script and documentation for configuring a basic firewall using **UFW (Uncomplicated Firewall)** on Linux.

---

## What is a Firewall?
A **firewall** is a network security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules. It acts as a barrier between a trusted internal network and untrusted external networks (like the Internet), blocking unauthorized access while permitting legitimate communications.

---

## Applied Rules & Justifications

| Command / Rule | Port / Protocol | Action | Justification / Purpose |
| :--- | :--- | :--- | :--- |
| `sudo ufw default deny incoming` | All Incoming | **DENY** | Enforces the Principle of Least Privilege by blocking all unsolicited inbound connections by default. |
| `sudo ufw allow ssh` | 22 / TCP | **ALLOW** | Ensures administrators can retain remote terminal control over the system. |
| `sudo ufw deny http` | 80 / TCP | **DENY** | Prevents unencrypted plain-text HTTP Web traffic to enforce secure web standards. |
| `sudo ufw allow https` | 443 / TCP | **ALLOW** | Permits secure, encrypted web traffic over SSL/TLS. |
| `sudo ufw deny from 192.168.1.100/32` | Any | **DENY** | Demonstrates host-based IP blocking to isolate or prevent traffic from a specific untrusted IP address. |

---

## Script Execution
To execute the firewall configuration script automatically:

```bash
chmod +x ufw_configuration.sh
sudo ./ufw_configuration.sh