---
title: "1.1_network_infrastructure.net"
date: 2025-06-21T09:21:40Z
draft: false
toc: false
images:
tags:
  - Computer Networks
---

# 1  Network Devices

## 1.1  Layer 1 Devices
- **Analog modem**: Developed to create connections between network segments via PSTN using POTS. Provides single connection (56Kbps max).  
- **Hub**: Functions as a concentrator/repeater. Operates in half-duplex, creates single collision domain. Mostly obsolete.

## 1.2  Layer 2 Devices
- **Switch**: Uses ASIC chips to learn MAC addresses and forward frames intelligently. Creates separate collision domains per port.  
- **Wireless Access Point (WAP)**: Bridges wireless and wired networks. Implements 802.11 standards (Wi-Fi 6, etc.).

## 1.3  Layer 3 Devices
- **Multilayer Switch (MLS)**: Combines Layer 2 switching with Layer 3 routing capabilities. High-performance but expensive.  
- **Router**: Connects different networks using IP addressing. Maintains routing tables (static/dynamic routes).

## 1.4  Optimization / Specialty Devices
- **Load Balancer**: Distributes traffic across servers (Round Robin, Least Connections).  
- **Proxy Server**: Intermediary for client requests (Forward/Reverse proxies).

---

# 2  Cabling & Media

## 2.1  Twisted-Pair Cabling
- **UTP**: Unshielded (Cat5/6)  
- **STP**: Shielded (industrial environments)  
- **Plenum**: Fire-retardant jacket  
- **Cable Types**:  
  - **Straight-through**: Host to switch  
  - **Crossover**: Like devices (e.g., switch to switch)  
  - **Rollover**: Console access (used with serial connections)

### 2.1.1  Connectors
- **RJ11**: 6P2C, used for telephone connections  
- **RJ45**: 8P8C, used for Ethernet networking  
- **66/110 Block**: Punch-down blocks used in structured cabling  
- **Serial (DB9/DB25)**: Legacy connectors for console and serial data

### 2.1.2  Categories
- **Cat5**: 100 MHz, up to 100 Mbps (obsolete)  
- **Cat5e**: 100 MHz, up to 1 Gbps  
- **Cat6**: 250 MHz, up to 10 Gbps (up to 55 m)  
- **Cat6a**: 500 MHz, up to 10 Gbps (up to 100 m)

---

## 2.2  Coaxial Cabling
- **Shielded Core**: Central copper conductor with insulating layer and metallic shield  
- **Use Cases**: Cable TV, broadband internet, CCTV

### 2.2.1  Cable Types
- **RG-6**: Modern standard for TV/Internet; thicker, less signal loss  
- **RG-59**: Older CCTV applications; thinner, more signal loss  
- **RG-11**: Best for long-distance runs; thick and less flexible

### 2.2.2  Connectors
- **BNC**: Quick-connect used in CCTV and legacy Ethernet  
- **F-type**: Screw-type connector for TV and modems  
- **N-type**: Durable connector for outdoor and industrial RF use

---

## 2.3  Fiber-Optic Cabling
- **Glass or Plastic Core**: Transmits light signals instead of electricity  
- **Use Cases**: High-speed LANs, WANs, backbone cabling

### 2.3.1  Cable Types
- **Single-mode (SMF)**: 9 µm core, laser light, long-range (up to 100 km)  
- **Multi-mode (MMF)**: 50/62.5 µm core, LED light, short-range (up to 2 km)

### 2.3.2  Connectors
- **LC** · **SC** · **ST** · **MTP/MPO**

---

## 2.4  Media Converters
Devices that allow different types of media to interconnect (e.g., copper to fiber). Useful in extending network distances or integrating older equipment.
- **Copper-to-Fiber**: Converts electrical signals to optical  
- **Single-mode to Multi-mode**: Adapts fiber types  
- **Bidirectional (BiDi)**: Uses a single fiber strand for TX/RX  
- **Managed vs Unmanaged**: Managed converters offer SNMP/monitoring

## 2.5  Cabling Tools
- **Crimpers** · **Wire strippers** · **Punch-down tool** · **Cable tester**  
- **TDR (Time Domain Reflectometer)** – tests copper length/breaks  
- **OTDR (Optical Time Domain Reflectometer)** – tests fiber length/loss

## 2.6  Wired-Ethernet Standards
| Standard | Medium | Speed | Max Distance |
|----------|--------|-------|--------------|
| **10BASE-T** | Cat3 UTP | 10 Mb/s | 100 m |
| **100BASE-TX** | Cat5 UTP | 100 Mb/s | 100 m |
| **1000BASE-T** | Cat5e/6 UTP | 1 Gb/s | 100 m |
| **10GBASE-T** | Cat6a/7 UTP | 10 Gb/s | 100 m |
| **1000BASE-LX** | SMF | 1 Gb/s | 5 km |
| **10GBASE-SR** | MMF | 10 Gb/s | 300 m |

---

# 3  WAN Technologies

## 3.1  PSTN
- **Dial-up**: 56 Kbps max (POTS)  
- **ISDN**: Digital (128 Kbps, BRI/PRI)  
- **xDSL**: Digital Subscriber Line variants:  
  - **ADSL** – Asymmetric (faster download)  
  - **VDSL** – Very-high-bit-rate (fiber hybrid)

## 3.2  Broadband
- **DOCSIS**: Cable modem standard (3.1 = 10 Gbps)  
- **Fiber**:  
  - **FTTH** – Fiber to Home  
  - **FTTC** – Fiber to Curb  
  - **FTTN** – Fiber to Node

## 3.3  Wireless WAN
- **Cellular**: 4G LTE, 5G (mmWave)  
- **WiMAX**: IEEE 802.16 (alternative to DSL)  
- **Satellite**: High latency (Geostationary/LEO)

## 3.4  Enterprise WAN
- **Metro Ethernet** – Ethernet over MAN  
- **Leased Lines** – T1 (1.544 Mbps), E1 (2.048 Mbps)  
- **MPLS** – Label switching for QoS  
- **Frame Relay** – Legacy packet-switched  
- **ATM** – Fixed 53-byte cells (obsolete)

## 3.5  WAN Components
| Component | Purpose & Key Points |
|-----------|---------------------|
| **Copper line drivers / Repeaters** | Boost and reshape attenuated electrical signals on long copper runs (e.g., T-carriers, DSL) to extend distance and reduce bit errors. |
| **Demarc (Demarcation Point)** | Legally defined hand-off between customer-premises equipment (CPE) and the service-provider network; responsibility for troubleshooting changes here. |
| **Network Interface Unit (NIU)** | Basic telco hand-off device; presents RJ-11/RJ-45, offers surge protection, simple loopback testing. |
| **Smartjack** | Enhanced NIU that adds diagnostics such as remote loopback, performance LEDs, and signal conditioning; common on T1/E1 circuits. |
| **CSU/DSU** | Channel Service Unit/Data Service Unit; converts router serial signals to provider’s digital framing, supplies clocking, line coding, and loopback tests. |

---

# 4  Topologies & Scope

## 4.1  Network Topologies
Peer-to-peer · Client/server · **Hybrid** · Bus · Ring · Star · Mesh · Point-to-point · Point-to-multipoint · **MPLS** (logical overlay)

## 4.2  Infrastructure Implementations
- **PAN** (Personal Area Network) – Bluetooth, USB tethering  
- **LAN** (Local Area Network) – Single building or campus  
- **MAN** (Metropolitan Area Network) – City-scale  
- **WAN** (Wide Area Network) – Large geographic area / Internet  
- **SCADA** – Industrial control (power plants, water treatment)  
- **Medianet** – Cisco term for media-optimized networks

---

# 5  Switching Concepts

Switches are Layer 2 (and sometimes Layer 3) devices that forward Ethernet frames based on MAC addresses. They are essential for connecting devices within a LAN and for creating efficient, collision-free communication paths.

## 5.1  Unmanaged vs. Managed Switches
Unmanaged switches are plug-and-play and offer no configuration capabilities (small/home networks).  
Managed switches provide VLANs, STP, traffic monitoring, SNMP, port mirroring, etc. (enterprise/complex networks).

## 5.2  Spanning Tree Protocol
STP prevents loops in Layer 2 networks by detecting redundant paths and selectively blocking ports. Variants: **RSTP**, **MSTP** (faster convergence, multiple trees).

## 5.3  Switch Port Types
- **Access ports** – carry traffic for a single VLAN  
- **Trunk ports** – carry multiple VLANs using tagging  
- **Mirrored ports** – replicate traffic for monitoring/analysis

## 5.4  VLANs
Virtual LANs logically segment a network into isolated domains, improving security, manageability, and traffic isolation.

## 5.5  Trunking
Allows multiple VLANs to traverse a single physical link (IEEE 802.1Q tagging).

## 5.6  Port Bonding (Link Aggregation / EtherChannel)
Combines multiple physical interfaces into one logical link—higher bandwidth and redundancy.

## 5.7  Power over Ethernet (PoE)
Delivers electrical power and data over one Ethernet cable; common for APs, IP phones, surveillance cameras.

## 5.8  Port Mirroring
Duplicates traffic from one or more switch ports to another port for IDS, packet capture, or diagnostics.

---
