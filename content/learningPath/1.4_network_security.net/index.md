---
title: "1.4_network_security.net"
date: 2025-06-21T09:22:29Z
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*Comprehensive reference of network-security devices, weaknesses, threats, hardening tactics, tooling, and physical safeguards—**all original material preserved, only rearranged for clearer flow**.*

---

# 1  Defensive Infrastructure

## 1.1  Security Devices
### Firewall  
Operates at Layers 2-4 and 7 with two inspection methods:  
- **Stateless** – ACL packet filtering  
- **Stateful** – Tracks connection state (more secure)

### Intrusion Detection System (IDS)  
- **Signature-Based** – Matches known attack patterns  
- **Anomaly-Based** – Detects deviations from baseline  
- **Policy-Based** – Enforces admin-defined rules

### Intrusion Prevention System (IPS)  
Inline system that can block malicious traffic, terminate connections, and quarantine hosts. Best placed between firewall and internal network.

### VPN Concentrator  
Manages multiple VPN connections  
- **Protocols**: IPsec, SSL/TLS  
- **Functions**: Authentication, encryption, access control  
- **Use cases**: Remote access, site-to-site VPNs

---

## 1.2  Firewall Basics

### Types of Firewalls
| Type                | Description                                      |
|---------------------|--------------------------------------------------|
| Packet Filtering    | Filters traffic by IP, port, protocol            |
| Stateful Inspection | Tracks connections and ensures stateful traffic  |
| Application Layer   | Filters traffic for specific applications        |
| Next-Gen Firewall   | Includes DPI, IDS/IPS, app awareness             |
| Host-based Firewall | Installed on devices (e.g., Windows Firewall)    |
| Network Firewall    | Protects entire segments (e.g., pfSense, Cisco)  |

### Firewall Settings & Techniques
- **Default-deny** policy (block all, allow explicitly)  
- Allow only necessary ports/IP ranges  
- Enable **NAT** to hide internal network  
- Integrate **IDS/IPS**  
- Enable logging & monitoring  
- Update firmware and apply patches regularly  

---

## 1.3  Network Access Control (NAC)
- Restricts access based on policies and device health  
- Integrates with **802.1X** and **RADIUS**  
- Enforces patch levels, antivirus status, device type  
- Detects and blocks rogue devices  
- Supports guest network segmentation

---

# 2  Vulnerabilities & Weak Practices

## 2.1  Common Network Vulnerabilities
Telnet • SNMPv1/v2 • FTP • TFTP • HTTP • SLIP

## 2.2  Vulnerable Network Practices
Unpatched or legacy systems • Open ports • Unnecessary services • Clear-text credentials • Unencrypted channels • RF emanation

---

# 3  Threat Taxonomy

## 3.1  Inside Threats
Malicious employee • Compromised system • Social engineering • ARP cache poisoning • Protocol/packet abuse • Man-in-the-middle • VLAN hopping

## 3.2  Outside Threats
Zero-day • Brute force • Spoofing • Session hijacking  
**Denial-of-Service Variants**  
- Traditional DoS  
- Permanent (PDoS)  
- Unintentional DoS  
- Distributed (DDoS)  
- Reflective DoS (DNS / NTP)  
- **Smurf** (ICMP broadcast amplification)

## 3.3  Wireless Network Threats
WPS brute force • War-driving/chalking • WEP/WPA cracking • Rogue AP • Evil twin • Bluejacking • Bluesnarfing

---

# 4  Hardening & Mitigation

## 4.1  Network Hardening Techniques

### 4.1.1  Secure Protocol Substitutions
| Insecure Protocol | Secure Alternative | Description                            |
|-------------------|--------------------|----------------------------------------|
| FTP               | **SFTP / FTPS**   | SSH- or SSL-secured file transfer      |
| Telnet            | **SSH**           | Encrypted remote terminal              |
| HTTP              | **HTTPS**         | TLS-encrypted web traffic              |
| SNMPv1/v2         | **SNMPv3**        | Auth + encryption                      |
| POP3 / IMAP       | **POP3S / IMAPS** | Email over SSL/TLS                     |

### 4.1.2  Anti-Malware Software
Signature, heuristic/behavioral, real-time protection, auto-updates, centralized management  
*Examples*: Windows Defender, ESET, Malwarebytes, CrowdStrike

### 4.1.3  Switch / Router Security
Disable unused ports • MAC filtering • Port security • SSH-only mgmt • Change defaults • VLAN segmentation • SNMPv3 • Logging

### 4.1.4  Encryption Basics
Symmetric (AES, DES) • Asymmetric (RSA, ECC) • TLS/SSL • IPsec • Hashing (SHA-256/3)

### 4.1.5  Wireless Hardening
WPA3 (or WPA2-AES) • Disable WPS • Change default SSID/admin creds • MAC filtering • Client isolation • Firmware updates • Limit signal range

### 4.1.6  User Authentication Controls
Strong passwords • MFA • Account lockout • Remove stale accounts • Session timeout & re-auth

### 4.1.7  Authentication / Authorization Methods
- **PAP** – Plain-text, insecure  
- **CHAP** – Challenge-response hashing  
- **EAP** – Extensible framework (EAP-TLS, PEAP, etc.)  
- **Kerberos** – Ticket-based mutual auth (KDC)

---

# 5  Physical Security

## 5.1  Credential Workarounds
BIOS/UEFI passwords • Disable external boot • Full-disk encryption • Console access logging

## 5.2  Layered Physical Controls

| Tier | Measures |
|------|----------|
| **Basic** | Locked doors, cameras, alarms, cable management |
| **Intermediate** | Guards, card/RFID, mantraps, motion sensors, EMI/RFI shielding |
| **Advanced** | Biometrics, Faraday cages, hardened racks, fire suppression, UPS/generators |

**Four Ds**: *Deterrence • Detection • Delay • Response*

---

# 6  Practical Security Tools

| Tool | Primary Use |
|------|-------------|
| **Bettercap** | MITM, sniffing, packet manipulation, DNS spoofing ![Bettercap](bettercap.png) |
| **hping3** | Custom packet crafting, firewall testing, DoS simulation ![hping3](hping3.png) |
| **Scapy (Python)** | Packet crafting/sending/sniffing/fuzzing ![Scapy](scapy.png) |

---
