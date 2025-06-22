---
title: "1.0_computer_networks.net"
date: 2025-06-10T09:23:40-07:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*Computer networks rely on many devices, protocols, services, standards, etc. that enable us to communicate with one another.*

## OSI MODEL
The Open Systems Interconnection (OSI) Model was created to standardize and streamline communication between networked devices.

### OSI Reference Model
- **Layer 7 Application**: Provides network services directly to user applications (HTTP, FTP, SMTP)
- **Layer 6 Presentation**: Handles data formatting, encryption/decryption (SSL, JPEG)
- **Layer 5 Session**: Manages communication sessions between devices (RPC, NetBIOS)
- **Layer 4 Transport**: Ensures reliable data transfer (TCP, UDP)
- **Layer 3 Network**: Handles logical addressing and routing (IP, ICMP)
- **Layer 2 Data Link**: Physical addressing and error detection (Ethernet, MAC)
- **Layer 1 Physical**: Transmits raw bit streams over physical media (Copper, Fiber)

Most devices operate on more than one layer, but to determine which layer a device is operating on, you must first identify the highest layer it is functioning on.

## TCP/IP reference model
| Layer | Duties | Example Protocols / PDU |
|-------|--------|-------------------------|
| **Application** | User-level services, formatting, encryption, authentication | HTTP, FTP, DNS – **Data** |
| **Transport** | End-to-end delivery, segmentation, flow & error control | TCP, UDP – **Segment** |
| **Internet** | Logical addressing, routing, path selection | IPv4, IPv6, ICMP – **Packet** |
| **Network Access / Link** | Physical addressing, media access, framing | Ethernet, Wi-Fi, ARP – **Frame / Bit** |

---

## TCP and UDP
### Transport-layer overview
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
* Works at Internet layer but supports Transport.  
* Sends control & error messages (echo, destination unreachable, TTL exceeded).

---

## Numbering systems
| Base | Digits | Typical Use |
|------|--------|-------------|
| **Binary (2)** | 0-1 | IPv4 subnetting, MAC addresses |
| **Octal (8)** | 0-7 | Unix file permissions |
| **Decimal (10)** | 0-9 | Human-readable values |
| **Hexadecimal (16)** | 0-9, A-F | IPv6, MAC addresses, memory dumps |


## Conversion tables
| Binary | Octal | Decimal | Hex |
|--------|-------|---------|-----|
| 0000   | 0     | 0  | 0 |
| 0001   | 1     | 1  | 1 |
| 0010   | 2     | 2  | 2 |
| 0011   | 3     | 3  | 3 |
| 0100   | 4     | 4  | 4 |
| 0101   | 5     | 5  | 5 |
| 0110   | 6     | 6  | 6 |
| 0111   | 7     | 7  | 7 |
| 1000   | 10    | 8  | 8 |
| 1001   | 11    | 9  | 9 |
| 1010   | 12    | 10 | A |
| 1011   | 13    | 11 | B |
| 1100   | 14    | 12 | C |
| 1101   | 15    | 13 | D |
| 1110   | 16    | 14 | E |
| 1111   | 17    | 15 | F |

---

## Encapsulation
1. **Data** created in Application layer.  
2. **Segment** (TCP/UDP header added).  
3. **Packet** (IP header added).  
4. **Frame** (MAC header & trailer added).  
5. **Bits** placed onto physical medium.

## IP Addressing

### IPv4 Properties
- IPv4 uses 32-bit addresses written in dotted decimal notation (e.g., 192.168.1.1).
- It supports around 4.3 billion unique addresses.
- Each address has a network and host portion.
- Paired with a subnet mask to define network boundaries.

### Classes of IPv4 Addresses
- Class A: 0.0.0.0 – 127.255.255.255
- Class B: 128.0.0.0 – 191.255.255.255
- Class C: 192.0.0.0 – 223.255.255.255
- Class D: 224.0.0.0 – 239.255.255.255 (Multicast)
- Class E: 240.0.0.0 – 255.255.255.255 (Experimental)

### Classless IPv4 Addresses
- CIDR (Classless Inter-Domain Routing) replaces class-based addressing.
- Allows flexible subnetting with prefix notation (e.g., /24).
- Enables efficient IP allocation and route aggregation.

### Subnetting IPv4 Addresses
- Divides networks into smaller subnetworks.
- Reduces broadcast domains, improves performance and security.
- Key concepts: subnet mask, network ID, broadcast address, host range.

### IPv6 Address Structure
- IPv6 uses 128-bit hexadecimal addresses (e.g., 2001:0db8::1).
- Written in eight 16-bit blocks, compressed with "::" where applicable.
- Vast address space to accommodate modern internet growth.

### IPv6 Network Transmissions
- IPv6 supports:
  - Unicast (one-to-one)
  - Multicast (one-to-many)
  - Anycast (one-to-nearest)
- IPv6 does **not** use broadcast.

## Special IP Networking Concepts

### The Media Access Control Address
- MAC address is a unique hardware address assigned to NICs.
- 48-bit address in hexadecimal (e.g., 00:1A:2B:3C:4D:5E).
- Operates at Layer 2 of the OSI model.

### Collision Domains vs. Broadcast Domains
- **Collision domain**: where data packets can collide (typically within hubs).
- **Broadcast domain**: where a broadcast packet is propagated (limited by routers).
- Switches separate collision domains; routers separate broadcast domains.

### Types of Network Transmissions
- **Unicast**: one sender to one receiver.
- **Broadcast**: one sender to all devices (IPv4 only).
- **Multicast**: one sender to specific group.
- **Anycast**: one sender to the closest receiver (IPv6).


## Modulation
* Converts digital data to analog signals for transmission.  
* Common types: **ASK** (Amplitude Shift Keying), **FSK** (Frequency), **PSK** (Phase), **QAM** (Quadrature Amplitude).

---

## Network transmission concepts
* **Bandwidth** vs. **Throughput** vs. **Goodput**  
* **Latency** (propagation, processing, queuing)  
* **Jitter** (variance in delay)  
* **MTU** and fragmentation  
* **Unicast, Broadcast, Multicast, Anycast**

---

## CSMA/CD vs. CSMA/CA
| Feature | CSMA/CD | CSMA/CA |
|---------|---------|---------|
| Medium | Wired Ethernet (legacy half-duplex) | Wireless LAN (Wi-Fi) |
| Method | Detects collisions, then back-offs | Avoids collisions via RTS/CTS & NAV timers |
| Status | Obsolete on full-duplex links | Still essential for 802.11 |

---