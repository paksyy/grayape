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
- **Layer 7 – Application**: Provides network services directly to user applications (HTTP, FTP, SMTP)  
- **Layer 6 – Presentation**: Handles data formatting, encryption/decryption (SSL, JPEG)  
- **Layer 5 – Session**: Manages communication sessions between devices (RPC, NetBIOS)  
- **Layer 4 – Transport**: Ensures reliable data transfer (TCP, UDP)  
- **Layer 3 – Network**: Handles logical addressing and routing (IP, ICMP)  
- **Layer 2 – Data Link**: Physical addressing and error detection (Ethernet, MAC)  
- **Layer 1 – Physical**: Transmits raw bit streams over physical media (Copper, Fiber)  

Most devices operate on more than one layer, but to determine which layer a device is operating on, you must first identify the highest layer at which it functions.

---

## 1.2 TCP/IP Reference Model
| Layer | Duties | Example Protocols / PDU |
|-------|--------|-------------------------|
| **Application** | User-level services, formatting, encryption, authentication | HTTP, FTP, DNS – **Data** |
| **Transport**   | End-to-end delivery, segmentation, flow & error control     | TCP, UDP – **Segment** |
| **Internet**    | Logical addressing, routing, path selection                | IPv4, IPv6, ICMP – **Packet** |
| **Network Access / Link** | Physical addressing, media access, framing       | Ethernet, Wi-Fi, ARP – **Frame / Bit** |

---

# 2. Transport & Control Protocols

## 2.1 TCP and UDP

### Transport-Layer Overview
* Provides logical communication between processes on different hosts.  
* Multiplexes using port numbers.

### Introduction to **TCP**
* Connection-oriented (three-way handshake).  
* Reliable (ACKs, sequence numbers, retransmission, windowing).  
* Ordered byte stream.

### Introduction to **UDP**
* Connectionless, best-effort.  
* Low overhead; ideal for voice/video, DNS, DHCP.  
* No built-in flow or error control.

### Introduction to **ICMP**
* Operates at the Internet layer but supports Transport.  
* Sends control & error messages (echo, destination unreachable, TTL exceeded).

---

# 3. Numbering Systems & Conversions

## 3.1 Numbering Systems
| Base | Digits | Typical Use |
|------|--------|-------------|
| **Binary (2)**       | 0–1     | IPv4 subnetting, MAC addresses |
| **Octal (8)**        | 0–7     | Unix file permissions |
| **Decimal (10)**     | 0–9     | Human-readable values |
| **Hexadecimal (16)** | 0–9, A–F | IPv6, MAC addresses, memory dumps |

## 3.2 Conversion Table
| Binary | Octal | Decimal | Hex |
|--------|-------|---------|-----|
| 0000 | 0  | 0  | 0 |
| 0001 | 1  | 1  | 1 |
| 0010 | 2  | 2  | 2 |
| 0011 | 3  | 3  | 3 |
| 0100 | 4  | 4  | 4 |
| 0101 | 5  | 5  | 5 |
| 0110 | 6  | 6  | 6 |
| 0111 | 7  | 7  | 7 |
| 1000 | 10 | 8  | 8 |
| 1001 | 11 | 9  | 9 |
| 1010 | 12 | 10 | A |
| 1011 | 13 | 11 | B |
| 1100 | 14 | 12 | C |
| 1101 | 15 | 13 | D |
| 1110 | 16 | 14 | E |
| 1111 | 17 | 15 | F |

---

# 4. Encapsulation & Data Flow

## 4.1 Encapsulation Steps
1. **Data** created at the Application layer.  
2. **Segment** (TCP/UDP header added).  
3. **Packet** (IP header added).  
4. **Frame** (MAC header & trailer added).  
5. **Bits** placed onto the physical medium.

---

# 5. Addressing & IP Concepts

## 5.1 IPv4 Fundamentals
- IPv4 uses 32-bit addresses written in dotted-decimal notation (e.g., 192.168.1.1).  
- It supports about 4.3 billion unique addresses.  
- Each address has a network and host portion, paired with a subnet mask.

### Classes of IPv4 Addresses
- Class A: 0.0.0.0 – 127.255.255.255  
- Class B: 128.0.0.0 – 191.255.255.255  
- Class C: 192.0.0.0 – 223.255.255.255  
- Class D: 224.0.0.0 – 239.255.255.255 _(Multicast)_  
- Class E: 240.0.0.0 – 255.255.255.255 _(Experimental)_

### Classless IPv4 Addresses (CIDR)
- Replaces class-based addressing.  
- Allows flexible subnetting with prefix notation (e.g., /24).  
- Enables efficient IP allocation and route aggregation.

### Subnetting IPv4 Addresses
- Divides networks into smaller subnets.  
- Reduces broadcast domains, improves performance and security.  
- Key concepts: subnet mask, network ID, broadcast address, host range.

---

## 5.2 IPv6 Fundamentals

### IPv6 Address Structure
- IPv6 uses 128-bit hexadecimal addresses (e.g., 2001:0db8::1).  
- Written in eight 16-bit blocks, compressible with “::”.  
- Vast address space to accommodate modern Internet growth.

### IPv6 Transmission Types
- **Unicast** – one-to-one  
- **Multicast** – one-to-many  
- **Anycast** – one-to-nearest  
- IPv6 does **not** use broadcast.

---

## 5.3 Additional IP-Layer Concepts

### MAC Address (Media Access Control)
- Unique 48-bit hardware address (e.g., 00:1A:2B:3C:4D:5E).  
- Operates at Layer 2.

### Collision vs. Broadcast Domains
- **Collision domain**: where packets can collide (e.g., within hubs).  
- **Broadcast domain**: where a broadcast propagates (bounded by routers).  
- Switches break collision domains; routers break broadcast domains.

### Transmission Types Recap
- **Unicast** • **Broadcast** • **Multicast** • **Anycast**

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
| Feature | CSMA/CD | CSMA/CA |
|---------|---------|---------|
| Medium  | Wired Ethernet (half-duplex legacy) | Wireless LAN (Wi-Fi) |
| Method  | Detects collisions, then backs off | Avoids collisions via RTS/CTS & NAV timers |
| Status  | Obsolete on full-duplex links | Still essential for 802.11 |

---
