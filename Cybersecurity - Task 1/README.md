# Nmap Network Scanning & Enumeration Lab

## Project Overview
This repository documents network discovery, service version identification, and OS fingerprinting performed using **Nmap** on an authorized target host (`scanme.nmap.org`).

---

## Technical Fundamentals

### What is Nmap?
**Nmap (Network Mapper)** is a free tool used to discover devices connected to a network and find out which ports and services are open on them.

### Why Network Scanning Matters
Network scanning is the foundational phase of security auditing and attack surface management:
* **Asset Discovery:** Keeps track of active hardware devices connected to network boundaries.
* **Attack Surface Reduction:** Helps engineers identify unintended open ports and shut down unauthorized services.
* **Vulnerability Auditing:** Allows security teams to identify outdated or unpatched software versions before malicious actors exploit them.

### Ethical Use Guidelines
* **Explicit Authorization:** Network scanning must only be performed on systems you own or have received formal, written authorization to test.
* **Controlled Target Testing:** Scans should be executed inside isolated sandbox environments or authorized targets (such as `scanme.nmap.org`).
* **Legal Compliance:** Scanning unauthorized external networks or production environments is illegal under cybersecurity regulations (e.g., Computer Fraud and Abuse Act) and can trigger service disruptions or legal action.

---

## Installation Steps

### Debian / Ubuntu / ChromeOS Linux

NB : I WORKED IN A CROSTINI ON CHROMEBOOK

```bash
sudo apt update
sudo apt install nmap -y