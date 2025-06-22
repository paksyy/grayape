---
title: "1.4_network_security.net"
date: 2025-06-21T09:22:29-00:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

---
## Security Devices

### Firewall
Operates at Layers 2-4 and 7 with two inspection methods:
- **Stateless**: Simple packet filtering (ACLs)
- **Stateful**: Tracks connection state (more secure)

### Intrusion Detection System (IDS)
- **Signature-Based**: Matches known attack patterns
- **Anomaly-Based**: Detects deviations from baseline
- **Policy-Based**: Enforces admin-defined rules

### Intrusion Prevention System (IPS)
Active system that can:
- Block malicious traffic
- Terminate connections
- Quarantine hosts
Best placed between firewall and internal network.

### VPN Concentrator
Specialized device for managing multiple VPN connections:
- Protocols: IPsec, SSL/TLS
- Functions: Authentication, encryption, access control
- Use cases: Remote access, site-to-site VPNs


## Common Network Vulnerabilities

### Telnet
A protocol used for remote login to devices, but it sends data in plaintext. Vulnerable to sniffing and man-in-the-middle attacks. It is largely replaced by SSH.

### SNMPv1 and SNMPv2
Older versions of the Simple Network Management Protocol that do not offer encryption. SNMPv3 includes secure authentication and encryption features.

### FTP (File Transfer Protocol)
Used for transferring files between systems but lacks encryption, making it vulnerable to interception of credentials and data.

### TFTP (Trivial File Transfer Protocol)
A simple, unauthenticated version of FTP used mainly in LANs. Frequently exploited due to its lack of security features.

### HTTP
Used to deliver web pages, but it transmits data in plaintext. Susceptible to interception. HTTPS should be used instead to ensure encryption.

### SLIP (Serial Line Internet Protocol)
An outdated protocol used to encapsulate IP packets over serial lines. It lacks error correction, encryption, and is no longer in use in modern systems.

---

## Vulnerable Network Practices

### Unpatched or Legacy Systems
Older systems or those missing security updates are prone to exploitation through known vulnerabilities. Maintaining patch management policies is critical.

### Open Ports
Ports that are open unnecessarily can serve as entry points for attackers. Regular port scanning and firewall policies are used to limit exposure.

### Unnecessary Running Services
Services running on systems that are not needed can increase the attack surface. These should be disabled or removed.

### Clear Text Credentials
Credentials transmitted without encryption can be intercepted using sniffing tools. Use of encryption protocols (e.g., SSH, TLS) is mandatory.

### Unencrypted Channels
Communication channels (e.g., HTTP, Telnet) without encryption allow attackers to view and manipulate data in transit.

### RF Emanation
Radio Frequency signals emitted by devices can be intercepted to extract sensitive information (e.g., keyboard input or screen data). Shielding and secured zones can mitigate this.

---

## Common Network Threats

### Inside Threats

#### Malicious Employee
A trusted insider with malicious intent, often exploiting their access to steal data, sabotage systems, or exfiltrate information.

#### Compromised System
A system that has been taken over by malware or remote attackers, potentially being used for launching attacks within the network.

#### Social Engineering
Psychological manipulation that tricks users into giving up confidential information or performing unsafe actions. Common forms include phishing, vishing, and baiting.

#### ARP Cache Poisoning
An attacker sends forged ARP responses to associate their MAC address with another host’s IP, enabling them to intercept, modify, or stop data intended for that host.

#### Protocol or Packet Abuse
Malicious use of networking protocols to manipulate or overload devices, such as crafting malformed packets to bypass firewalls or crash systems.

#### Man-in-the-Middle Attack
The attacker secretly intercepts and possibly alters communication between two parties who believe they are directly communicating with each other.

#### VLAN Hopping
Exploiting network switch configurations to gain access to traffic on other VLANs, which are intended to be isolated from each other.

### Outside Threats

#### Zero-Day Attacks
Attacks that exploit previously unknown vulnerabilities for which no patch exists. Extremely dangerous and hard to defend against.

#### Brute Force Attacks
Systematic attempts to guess passwords or cryptographic keys by trying every possible combination.

#### Spoofing
Impersonating another device or user on a network, such as IP spoofing or email spoofing, to bypass access controls or spread malware.

#### Session Hijacking
Taking control of a user's active session by stealing or predicting session tokens, allowing attackers to impersonate them.

#### Denial of Service (DoS)

- **Traditional DoS:** Floods a target system with traffic, making it unavailable to legitimate users.
- **Permanent DoS (PDoS):** Destroys or corrupts hardware or firmware, requiring replacement.
- **Unintentional DoS:** Caused by configuration errors or legitimate use spikes.
- **Distributed DoS (DDoS):** Coordinated attacks from multiple sources (botnets).
- **Reflective DoS:** Exploits third-party servers to reflect and amplify traffic to the victim.
  - Reflective DNS
  - Reflective NTP
- **Smurf Attacks:** Exploits ICMP and broadcast addresses to amplify attacks using spoofed source IPs.

---

## Wireless Network Threats

### WPS (Wi-Fi Protected Setup)
A simplified wireless connection method that is vulnerable to brute-force attacks due to predictable PINs.

### War Driving / War Chalking
Scanning for unsecured wireless networks while driving. War chalking refers to marking these networks physically or digitally.

### WEP / WPA Cracking
Breaking weak encryption in outdated Wi-Fi protocols. WEP is especially vulnerable; WPA2 and WPA3 are preferred.

### Rogue Access Point
Unauthorized wireless access point set up to intercept traffic or lure users into connecting.

### Evil Twin Attack
A fake wireless AP mimicking a legitimate one to perform man-in-the-middle attacks on connected users.

### Bluejacking
Sending unsolicited messages to nearby Bluetooth devices. Not highly dangerous but often used to annoy or trick users.

### Bluesnarfing
Unauthorized access to data on a Bluetooth-enabled device. Can expose contacts, emails, files, etc.

---

## Practical Tools

### Bettercap
A powerful, modular network attack and monitoring tool capable of conducting MITM attacks, sniffing traffic, manipulating packets, DNS spoofing, and injecting code in real time. Supports plugins and scripting.

![Bettercap](bettercap.png)

### hping3
A network scanning and packet crafting tool used to generate custom TCP/IP packets. Commonly used for firewall testing, spoofing, and DoS simulations. Also useful in OS fingerprinting.

![hping3](hping3.png)

### Scapy (Python Library)
A powerful Python-based packet manipulation tool used for crafting, sending, sniffing, and analyzing network traffic. Supports multiple protocols and allows the creation of custom packet flows and fuzzing.

![Scapy](scapy.png)

---

## Network Hardening Techniques

Network hardening involves reducing vulnerabilities in your network infrastructure to protect against attacks and unauthorized access.

### Secure Protocols

Use **secure alternatives** to insecure network protocols:

| Insecure Protocol | Secure Alternative | Description                            |
|-------------------|--------------------|----------------------------------------|
| FTP               | SFTP / FTPS        | Secures file transfer with SSH or SSL  |
| Telnet            | SSH                | Encrypts remote terminal communication |
| HTTP              | HTTPS              | Encrypts web traffic using TLS         |
| SNMPv1/v2         | SNMPv3             | Adds authentication and encryption     |
| POP3 / IMAP       | POP3S / IMAPS      | Email protocols over SSL/TLS           |

### Anti-Malware Software

Protect endpoints and servers with:

- **Signature-based detection** (detects known threats)
- **Heuristic/Behavioral analysis** (detects unknown threats)
- **Real-time protection** (active scanning of file activity)
- **Automated updates** for malware definitions
- **Centralized management** for enterprise deployments

**Examples**: Windows Defender, ESET, Malwarebytes, CrowdStrike

### Switch and Router Security Measures

- Disable unused ports and interfaces
- Use MAC address filtering
- Enable port security (limit number of MACs per port)
- Allow SSH access only (disable Telnet)
- Change all default usernames and passwords
- Use VLANs for network segmentation
- Enable logging and use SNMPv3 for secure monitoring

### Encryption Basics

- **Symmetric encryption**: One shared key (e.g., AES, DES)
- **Asymmetric encryption**: Public/private key pair (e.g., RSA, ECC)
- **TLS/SSL**: Encrypts traffic for secure communications
- **IPsec**: Encrypts network traffic (used in VPNs)
- **Hashing**: Ensures data integrity (SHA-256, SHA-3)

### Wireless Network Hardening

- Use **WPA3** (or at least WPA2 with AES)
- Disable **WPS** to prevent brute-force attacks
- Change default **SSID** and admin credentials
- Enable **MAC filtering**
- Use **client isolation** on guest/public networks
- Apply **firmware updates** regularly
- Limit **signal range** to control exposure

### User Authentication

- Enforce strong password policies
- Implement multi-factor authentication (MFA)
- Apply account lockout after multiple failures
- Audit and disable unused accounts regularly
- Use session timeouts and re-authentication

### Authentication and Authorization Methods

- **PAP (Password Authentication Protocol)**  
  Sends credentials in plaintext. Insecure and outdated.

- **CHAP (Challenge Handshake Authentication Protocol)**  
  Uses challenge-response and hashing. More secure than PAP.

- **EAP (Extensible Authentication Protocol)**  
  Framework for multiple authentication types (e.g., EAP-TLS, EAP-TTLS, PEAP). Common in WPA2/WPA3 Enterprise and 802.1X.

- **Kerberos**  
  Ticket-based mutual authentication using a **Key Distribution Center (KDC)**. Common in Active Directory environments.

---

## Physical Network Security

Secure the physical infrastructure against unauthorized access, damage, or theft.

### Credential Workaround

- Set BIOS/UEFI passwords
- Disable booting from USB or CD devices
- Encrypt drives (e.g., BitLocker, LUKS)
- Monitor and log access to devices and consoles

### Basic Physical Security

- Locked doors to server/network rooms
- Surveillance cameras
- Alarm systems
- Cable management to prevent tampering

### Intermediate Physical Security

- Security guards and access controls
- Access cards and RFID key fobs
- Mantraps (double door entry)
- Motion detectors
- EMI/RFI shielding for cables

### Advanced Physical Security

- Biometric access (fingerprint, iris)
- Faraday cages for sensitive hardware
- Hardened server racks/cabinets
- Fire suppression and climate control systems
- Backup power (UPS/generators)

### Methods of Physical Security

- **Deterrence**: Cameras, lighting
- **Detection**: Sensors, surveillance
- **Delay**: Locks, reinforced doors
- **Response**: Security staff, alarm systems

---

## Firewall Basics

Firewalls monitor and control incoming and outgoing traffic based on defined security rules.

### Types of Firewalls

| Type                | Description                                      |
|---------------------|--------------------------------------------------|
| Packet Filtering    | Filters traffic by IP, port, protocol            |
| Stateful Inspection | Tracks connections and ensures stateful traffic |
| Application Layer   | Filters traffic for specific applications        |
| Next-Gen Firewall   | Includes DPI, IDS/IPS, app awareness             |
| Host-based Firewall | Installed on devices (e.g., Windows Firewall)    |
| Network Firewall    | Protects entire segments (e.g., pfSense, Cisco)  |

### Firewall Settings and Techniques

- Use a **default deny** policy (block all, allow explicitly)
- Only allow necessary ports and IP ranges
- Enable **NAT** to hide internal network
- Configure **intrusion detection/prevention (IDS/IPS)**
- Enable **logging and monitoring**
- Update firmware and apply patches regularly

---

## Network Access Control (NAC)

- Restricts network access based on policies and device health
- Integrates with **802.1X** and **RADIUS servers**
- Enforces patch levels, antivirus status, device type
- Helps detect and block **rogue devices**
- Supports **guest network segmentation**

---



