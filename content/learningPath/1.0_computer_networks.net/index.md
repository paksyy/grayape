---

title: "1.0_computer_networks.net"
date: 2025-06-10T09:23:40-07:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*Computer networks rely on many devices, protocols, services, and standards that enable us to communicate with one another.*

---

# 1. Reference Models & Architecture

## 1.1 OSI Model

The Open Systems Interconnection (OSI) Model was created to standardize and streamline communication between networked devices.

### OSI Reference Model

* **Layer 7 – Application**: Provides network services directly to user applications (HTTP, FTP, SMTP)
* **Layer 6 – Presentation**: Handles data formatting, encryption/decryption (SSL, JPEG)
* **Layer 5 – Session**: Manages communication sessions between devices (RPC, NetBIOS)
* **Layer 4 – Transport**: Ensures reliable data transfer (TCP, UDP)
* **Layer 3 – Network**: Handles logical addressing and routing (IP, ICMP)
* **Layer 2 – Data Link**: Physical addressing and error detection (Ethernet, MAC)
* **Layer 1 – Physical**: Transmits raw bit streams over physical media (Copper, Fiber)

Most devices operate on more than one layer, but to determine which layer a device is operating on, you must first identify the highest layer at which it functions.

---

## 1.2 TCP/IP Reference Model

| Layer                     | Duties                                                      | Example Protocols / PDU                |
| ------------------------- | ----------------------------------------------------------- | -------------------------------------- |
| **Application**           | User‑level services, formatting, encryption, authentication | HTTP, FTP, DNS – **Data**              |
| **Transport**             | End‑to‑end delivery, segmentation, flow & error control     | TCP, UDP – **Segment**                 |
| **Internet**              | Logical addressing, routing, path selection                 | IPv4, IPv6, ICMP – **Packet**          |
| **Network Access / Link** | Physical addressing, media access, framing                  | Ethernet, Wi‑Fi, ARP – **Frame / Bit** |

---

## 1.3 OSI vs. TCP/IP Side‑by‑Side

| OSI (7)      | TCP/IP (4)     | Typical PDU |
| ------------ | -------------- | ----------- |
| Application  | Application    | **Data**    |
| Presentation | Application    |             |
| Session      | Application    |             |
| Transport    | Transport      | **Segment** |
| Network      | Internet       | **Packet**  |
| Data‑Link    | Network Access | **Frame**   |
| Physical     | Network Access | **Bits**    |

> **Tip:** The three upper‑layer OSI functions (Presentation, Session, Application) are grouped into a single *Application* layer in the TCP/IP model.

---

## 1.4 Device & PDU Quick Reference

| OSI Layer        | PDU     | Common Devices                                       |
| ---------------- | ------- | ---------------------------------------------------- |
| 7‑5 Upper Layers | Data    | **Proxy server**, **Web server**, **DNS server**     |
| 4 Transport      | Segment | **Load balancer**, **Firewall ALG**                  |
| 3 Network        | Packet  | **Router**, **Layer‑3 switch**, **VPN concentrator** |
| 2 Data‑Link      | Frame   | **Switch**, **Wireless AP**, **Bridge**              |
| 1 Physical       | Bits    | **Hub**, **Media converter**, **Transceiver**        |

*(See `1.1_network_infrastructure.net` for deep dives into each device.)*

---

# 2. Transport & Control Protocols

## 2.1 TCP, UDP & ICMP

### 2.1.1 Transport‑Layer Overview

* Provides logical communication between processes on different hosts.
* Multiplexes using port numbers.

### 2.1.2 TCP Essentials

* **Connection‑oriented** – three‑way handshake (SYN → SYN/ACK → ACK).
* **Reliable** – sequence numbers, ACKs, retransmission, sliding window.
* **Ordered** byte stream.

#### TCP Flag Cheat Sheet

| Flag    | Purpose                             |
| ------- | ----------------------------------- |
| **SYN** | Start connection, synchronize seq # |
| **ACK** | Acknowledgment of received data     |
| **FIN** | Gracefully close connection         |
| **RST** | Abort connection immediately        |
| **PSH** | Push buffered data to application   |
| **URG** | Urgent pointer field significant    |

> The classic **three‑way handshake** uses SYN and ACK; termination typically uses FIN/ACK pairs.

#### Congestion‑Control in One Paragraph

TCP adjusts its **congestion window (cwnd)** using *slow start* and *additive‑increase/multiplicative‑decrease (AIMD)* to probe available bandwidth, backing off when packet loss implies congestion.

### 2.1.3 UDP Essentials

* **Connectionless**, best‑effort delivery.
* Low overhead; ideal for voice/video (VoIP), DNS, DHCP.
* No built‑in flow or error control.

### 2.1.4 ICMP Essentials

* Sends control & error messages (echo request/reply, destination unreachable, TTL exceeded).

#### Common ICMP Type/Code Values

| Type | Code | Meaning                                 |
| ---- | ---- | --------------------------------------- |
| 0    | 0    | Echo Reply                              |
| 3    | 0‑15 | Destination Unreachable sub‑codes       |
| 8    | 0    | Echo Request                            |
| 11   | 0‑1  | Time Exceeded (TTL/fragment reassembly) |

---

## 2.2 Well‑Known Ports

| Port        | Protocol | Typical Service    |
| ----------- | -------- | ------------------ |
| **20/21**   | TCP      | FTP data/control   |
| **22**      | TCP      | SSH / SFTP         |
| **23**      | TCP      | Telnet (legacy)    |
| **25**      | TCP      | SMTP               |
| **53**      | UDP/TCP  | DNS                |
| **67/68**   | UDP      | DHCP server/client |
| **80**      | TCP      | HTTP               |
| **110**     | TCP      | POP3               |
| **123**     | UDP      | NTP                |
| **143**     | TCP      | IMAP               |
| **161/162** | UDP      | SNMP               |
| **389**     | TCP/UDP  | LDAP               |
| **443**     | TCP      | HTTPS              |
| **587**     | TCP      | SMTP submission    |
| **993**     | TCP      | IMAPS              |
| **3389**    | TCP      | RDP                |

---

# 3. Numbering Systems & Conversions

## 3.1 Numbering Systems

| Base                 | Digits   | Typical Use                       |
| -------------------- | -------- | --------------------------------- |
| **Binary (2)**       | 0–1      | IPv4 subnetting, MAC addresses    |
| **Octal (8)**        | 0–7      | Unix file permissions             |
| **Decimal (10)**     | 0–9      | Human‑readable values             |
| **Hexadecimal (16)** | 0–9, A–F | IPv6, MAC addresses, memory dumps |

## 3.2 Conversion Table

| Binary | Octal | Decimal | Hex |
| ------ | ----- | ------- | --- |
| 0000   | 0     | 0       | 0   |
| 0001   | 1     | 1       | 1   |
| 0010   | 2     | 2       | 2   |
| 0011   | 3     | 3       | 3   |
| 0100   | 4     | 4       | 4   |
| 0101   | 5     | 5       | 5   |
| 0110   | 6     | 6       | 6   |
| 0111   | 7     | 7       | 7   |
| 1000   | 10    | 8       | 8   |
| 1001   | 11    | 9       | 9   |
| 1010   | 12    | 10      | A   |
| 1011   | 13    | 11      | B   |
| 1100   | 14    | 12      | C   |
| 1101   | 15    | 13      | D   |
| 1110   | 16    | 14      | E   |
| 1111   | 17    | 15      | F   |

---

# 4. Encapsulation & Data Flow

## 4.1 Encapsulation Steps

1. **Data** created at the Application layer.
2. **Segment** (TCP/UDP header added).
3. **Packet** (IP header added).
4. **Frame** (MAC header & trailer added).
5. **Bits** placed onto the physical medium.

## 4.2 Visualising Encapsulation

```
Application ▸ Presentation ▸ Session ▸ Transport ▸ Network ▸ Data‑Link ▸ Physical
      Data ▸            Segment ▸      Packet ▸        Frame ▸            Bits
```

*(Lines show the journey down the stack during transmit; on reception the order is reversed.)*

---

# 5. Addressing & IP Concepts

## 5.1 IPv4 Fundamentals

* IPv4 uses 32‑bit addresses written in dotted‑decimal notation (e.g., 192.168.1.1).
* Supports about 4.3 billion unique addresses.
* Each address has a network and host portion, paired with a subnet mask.

### Classes of IPv4 Addresses

* Class A: 0.0.0.0 – 127.255.255.255
* Class B: 128.0.0.0 – 191.255.255.255
* Class C: 192.0.0.0 – 223.255.255.255
* Class D: 224.0.0.0 – 239.255.255.255 *(Multicast)*
* Class E: 240.0.0.0 – 255.255.255.255 *(Experimental)*

### Private & APIPA Ranges

| Purpose       | CIDR           | Range                         |
| ------------- | -------------- | ----------------------------- |
| **Private A** | 10.0.0.0/8     | 10.0.0.0 – 10.255.255.255     |
| **Private B** | 172.16.0.0/12  | 172.16.0.0 – 172.31.255.255   |
| **Private C** | 192.168.0.0/16 | 192.168.0.0 – 192.168.255.255 |
| **APIPA**     | 169.254.0.0/16 | 169.254.0.0 – 169.254.255.255 |

### Classless IPv4 Addresses (CIDR)

* Replaces class‑based addressing.
* Allows flexible subnetting with prefix notation (e.g., /24).
* Enables efficient IP allocation and route aggregation.

### Subnetting IPv4 Addresses

* Divides networks into smaller subnets.
* Reduces broadcast domains, improves performance and security.
* Key concepts: subnet mask, network ID, broadcast address, host range.

### IPv4 Header Essentials

| Field                                    | Bits    | Purpose                     |
| ---------------------------------------- | ------- | --------------------------- |
| Version                                  | 4       | IP version (4)              |
| IHL                                      | 4       | Header length               |
| Total Length                             | 16      | Entire packet size          |
| Identification / Flags / Fragment Offset | 32      | Fragmentation control       |
| TTL                                      | 8       | Packet lifespan             |
| Protocol                                 | 8       | Upper‑layer (TCP=6, UDP=17) |
| Header Checksum                          | 16      | Error check of header       |
| Source / Destination Address             | 32 + 32 | Sender / receiver IP        |

### Fragmentation & Path‑MTU Discovery

If a packet exceeds the **Maximum Transmission Unit (MTU)** of a link, IPv4 can fragment it (unless *Don’t Fragment* flag set). Modern hosts prefer **PMTUD** to learn the smallest MTU along a path and avoid fragmentation.

---

## 5.2 IPv6 Fundamentals

### IPv6 Address Structure

* 128‑bit hexadecimal addresses (e.g., 2001:0db8::1).
* Written in eight 16‑bit blocks, compressible with “::”.
* Vast address space to accommodate modern Internet growth.

### IPv6 Transmission Types

* **Unicast** – one‑to‑one
* **Multicast** – one‑to‑many
* **Anycast** – one‑to‑nearest
* IPv6 does **not** use broadcast.

### IPv6 Header Essentials

| Field                        | Bits      | Purpose                         |
| ---------------------------- | --------- | ------------------------------- |
| Version                      | 4         | IP version (6)                  |
| Traffic Class                | 8         | QoS markings                    |
| Flow Label                   | 20        | Identify packet flows           |
| Payload Length               | 16        | Size of data after header       |
| Next Header                  | 8         | Upper‑layer or extension header |
| Hop Limit                    | 8         | IPv6 TTL equivalent             |
| Source / Destination Address | 128 + 128 | Sender / receiver IPv6          |

---

## 5.3 Additional IP‑Layer Concepts

### MAC Address (Media Access Control)

* Unique 48‑bit hardware address (e.g., 00:1A:2B:3C:4D:5E).
* Operates at Layer 2.

### Collision vs. Broadcast Domains

* **Collision domain**: where packets can collide (e.g., within hubs).
* **Broadcast domain**: where a broadcast propagates (bounded by routers).
* Switches break collision domains; routers break broadcast domains.

### Transmission Types Recap

* **Unicast** • **Broadcast** • **Multicast** • **Anycast**

---

# 6. Physical Layer & Media Access

## 6.1 Modulation

Converts digital data to analog signals for transmission.
Common methods: **ASK**, **FSK**, **PSK**, **QAM**.

## 6.2 Network Transmission Metrics

* **Bandwidth** vs. **Throughput** vs. **Goodput**
* **Latency** (propagation, processing, queuing)
* **Jitter** (variation in delay)
* **MTU** and fragmentation

## 6.3 CSMA/CD vs. CSMA/CA

| Feature | CSMA/CD                             | CSMA/CA                                    |
| ------- | ----------------------------------- | ------------------------------------------ |
| Medium  | Wired Ethernet (half‑duplex legacy) | Wireless LAN (Wi‑Fi)                       |
| Method  | Detects collisions, then backs off  | Avoids collisions via RTS/CTS & NAV timers |
| Status  | Obsolete on full‑duplex links       | Still essential for 802.11                 |

---

# 7. Quick Lab Tips

* `ping -c 4 <host>` – basic reachability & RTT.
* `traceroute <host>` – view hop path & latency per hop.
* `ip addr`, `ip -6 route`, `ss -tulpn` – inspect interfaces, routing, open sockets.