---
title: "1.2_network_services_&_protocols.net"
date: 2025-06-21T09:22:23-00:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

## DHCP
Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automatically assign IP addresses and other network configuration parameters to client devices. It simplifies network management by reducing the need for manual IP configuration.

- **Static IP**: Manually configured IP address that does not change over time. Useful for servers, printers, and other critical devices.
- **Dynamic IP**: Automatically assigned by the DHCP server from a predefined pool. The address may change when the lease expires or the device reconnects.
- **DHCP Process (DORA)**:
  - **Discover**: Client sends broadcast request to locate a DHCP server.
  - **Offer**: Server responds with an available IP address and configuration options.
  - **Request**: Client requests the offered IP from one of the servers.
  - **Acknowledgment**: Server confirms the lease and completes the configuration.
- **Ports**: DHCP communication uses **UDP port 67** (server) and **UDP port 68** (client).
- **Leases**: IP addresses are assigned for a limited period (lease time). Clients must renew leases before expiration to keep their IPs.
- **Options**: Additional parameters provided by the DHCP server, such as default gateway, DNS servers, domain name, NTP servers, and more.
- **Preferred IP configuration**: Clients can request a specific IP address, and the server may honor the request if available.
- **DHCP Relay (IP Helper)**: Allows DHCP requests to be forwarded across subnets to a central DHCP server. Common in large networks to avoid deploying a DHCP server per subnet.

## DNS
The Domain Name System (DNS) translates domain names into IP addresses. It is a critical component of network communication and internet functionality.

- **Servers**: Include root, TLD, authoritative, and caching resolvers. Resolve queries from users to locate websites or services.
- **Records**:
  - **A/AAAA**: IPv4/IPv6 address records.
  - **CNAME**: Alias for another domain.
  - **MX**: Mail exchange server.
  - **NS**: Delegates a subdomain to a DNS server.
  - **PTR**: Reverse DNS mapping.
  - **TXT**: Text records (e.g., SPF, DKIM).
- **Dynamic DNS**: Automatically updates DNS records in real-time when devices join or leave the network, useful in environments with frequently changing IPs.

## NAT (Network Address Translation)
- **Static NAT**: 1:1 mapping (public:private)
- **Dynamic NAT**: Pool of public addresses
- **PAT (Port NAT)**: Many private to single public
- **Address Types**: Public/Private, RFC 1918

---

## (PRACTICAL) Service Enumeration
Tools used for querying, discovering, and enumerating information about services, particularly DNS and web services:

- **dig**: A powerful DNS lookup tool for querying specific DNS records and analyzing DNS responses.

  ![dig](dig.png)

- **dnsrecon**: Python-based tool for performing DNS enumeration, including brute force, zone transfers, and record collection.

  ![dnsrecon](dnsrecon.png)

- **curl**: Transfers data from or to a server using supported protocols (HTTP, FTP, etc.), ideal for testing endpoints.

  ![curl](curl.png)
  
- **wget**: Retrieves content from web servers, often used for downloading files or mirroring websites.

  ![wget](wget.png)

---

## Network Access Applications
- **VPN**: Secure remote access (IPsec, SSL)
- **Remote Access**: RDP, SSH, Telnet
- **Web Services**: HTTP/HTTPS, REST APIs
- **Unified Voice**: VoIP, SIP trunking

## VPN Protocols
- **IPsec**: Secure encrypted tunnels (IKE, ESP)
- **GRE**: Generic Routing Encapsulation (no encryption)
- **PPTP**: Obsolete (MS-CHAP vulnerabilities)
- **TLS/SSL**: Common in web-based VPNs

## Network Access Services
- **NIC**: Network Interface Card (Physical/MAC address)
- **RADIUS**: Centralized authentication (UDP 1812)
- **TACACS+**: Cisco alternative (TCP 49, more secure)

---

## Routing

### Static Routing
- Routes are manually configured by an admin.
- Simple but not scalable; no automatic path updates.

### Dynamic Routing
- Routers learn routes from each other automatically.
- Uses protocols like OSPF, EIGRP, RIP, and BGP.

### Default Route
- A catch-all route when no specific match is found.
- Usually points to the internet gateway.
- Represented as `0.0.0.0/0` or `::/0`.

### Routing Table
- Stores all known routes to destination networks.
- Includes static, dynamic, and default routes.

### Loopback Interface
- A virtual interface used for diagnostics and stability.
- IPv4: 127.0.0.1, IPv6: ::1

### Routing Loop
- A situation where packets endlessly circulate due to misconfiguration.
- Prevented using TTL, split horizon, or route poisoning.

### Routing Metrics
- Values used to determine the best route.
- Includes hop count, bandwidth, delay, reliability, and cost.

### Routing Aggregation
- Combines multiple routes into one summary route.
- Reduces routing table size and simplifies configuration.

### High Availability
- Ensures continuous network operation through redundancy.
- Technologies: VRRP, HSRP, GLBP, failover routing, load balancing.

## Routing Protocols

### IGP (Interior Gateway Protocol)
- IGPs are used for routing **within a single autonomous system (AS)**.
- Designed for internal network communication and fast convergence.
- Common IGPs:
  - **RIP (Routing Information Protocol)** – Distance-vector, simple but limited.
  - **OSPF (Open Shortest Path First)** – Link-state, scalable, widely used.
  - **EIGRP (Enhanced Interior Gateway Routing Protocol)** – Cisco proprietary, advanced distance-vector.

### EGP (Exterior Gateway Protocol)
- EGPs are used for routing **between autonomous systems**, usually across the internet.
- The primary EGP is:
  - **BGP (Border Gateway Protocol)** – Path-vector protocol used by ISPs and enterprises to exchange routing information on the internet.
- EGPs focus on **policy-based routing** and scalability, rather than speed of convergence.

---

## Unified communication

### Unified communication devices
Unified communication devices include hardware that enables integrated communications, such as IP phones, video conferencing systems, headsets, speakerphones, and collaboration hubs. These devices are optimized for services like VoIP, video calls, screen sharing, and real-time messaging.

Examples:
- IP desk phones with video support
- USB headsets with noise cancellation
- Smart conferencing cameras with tracking
- Interactive whiteboards

### Voice over IP
Voice over IP (VoIP) allows voice communication over the internet rather than traditional phone lines. It converts voice into digital packets and sends them over IP networks. VoIP reduces communication costs and enables integration with other services like video and chat.

Advantages:
- Lower cost than PSTN
- Integration with UC platforms
- Scalability and portability
- Advanced call features (voicemail-to-email, call routing, etc.)

Common VoIP Protocols:
- SIP (Session Initiation Protocol)
- RTP (Real-time Transport Protocol)
- H.323

## Networking protocols
* **Routing:** RIP, OSPF, EIGRP, BGP  
* **Secure remote access:** SSH, TLS, IPsec  
* **Management & monitoring:** SNMP, NetFlow, Syslog, NTP  
* **Name resolution:** DNS, mDNS  
* **Addressing/assignment:** DHCP, SLAAC  
* **Email:** SMTP, IMAP, POP3  
* **File transfer & sharing:** FTP, SFTP, SMB, NFS  
* **Web:** HTTP/HTTPS, QUIC  
* **Messaging:** MQTT, AMQP  