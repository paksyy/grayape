---
title: "1.1_network_infrastructure.net"
date: 2025-06-21T09:21:40-00:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

## Network Devices

### Layer 1 Devices:
- **Analog modem**: Developed to create connections between network segments via PSTN using POTS. Provides single connection (56Kbps max).
- **Hub**: Functions as a concentrator/repeater. Operates in half-duplex, creates single collision domain. Mostly obsolete.

### Layer 2 Devices:
- **Switch**: Uses ASIC chips to learn MAC addresses and forward frames intelligently. Creates separate collision domains per port.
- **Wireless Access Point (WAP)**: Bridges wireless and wired networks. Implements 802.11 standards (Wi-Fi 6, etc.).

### Layer 3 Devices:
- **Multilayer Switch (MLS)**: Combines Layer 2 switching with Layer 3 routing capabilities. High-performance but expensive.
- **Router**: Connects different networks using IP addressing. Maintains routing tables (static/dynamic routes).

## Optimization Devices
- **Load Balancer**: Distributes traffic across servers (Round Robin, Least Connections)
- **Proxy Server**: Intermediary for client requests (Forward/Reverse proxies)

---

## Network Cabling

### Twisted Pair
- **UTP**: Unshielded (Cat5/6)
- **STP**: Shielded (industrial environments)
- **Plenum**: Fire-retardant jacket
- **Cable Types**:
  - **Straight-through**: Host to switch
  - **Crossover**: Like devices (e.g., switch to switch)
  - **Rollover**: Console access (used with serial connections)

#### Connectors
- **RJ11**: 6P2C, used for telephone connections
- **RJ45**: 8P8C, used for Ethernet networking
- **66/110 Block**: Punch-down blocks used in structured cabling
- **Serial (DB9/DB25)**: Legacy connectors for console and serial data

#### Categories
- **Cat5**: 100 MHz, up to 100 Mbps (obsolete)
- **Cat5e**: 100 MHz, up to 1 Gbps
- **Cat6**: 250 MHz, up to 10 Gbps (up to 55m)
- **Cat6a**: 500 MHz, up to 10 Gbps (up to 100m)

### Coaxial Cabling
- **Shielded Core**: Central copper conductor with insulating layer and metallic shield
- **Use Cases**: Cable TV, broadband internet, CCTV

#### Cable Types
- **RG-6**: Modern standard for TV/Internet; thicker, less signal loss
- **RG-59**: Older CCTV applications; thinner, more signal loss
- **RG-11**: Best for long-distance runs; thick and less flexible

#### Connectors
- **BNC**: Quick-connect used in CCTV and legacy Ethernet
- **F-type**: Screw-type connector for TV and modems
- **N-type**: Durable connector for outdoor and industrial RF use

### Fiber Optic Cabling
- **Glass or Plastic Core**: Transmits light signals instead of electricity
- **Use Cases**: High-speed LANs, WANs, backbone cabling

#### Cable Types
- **Single-mode (SMF)**: 9µm core, laser light, long-range (up to 100km)
- **Multi-mode (MMF)**: 50/62.5µm core, LED light, short-range (up to 2km)

#### Connectors
- **LC**: Compact connector, common in data centers
- **SC**: Push-pull connector, widely used in telecom
- **ST**: Twist-lock connector, used in legacy fiber systems
- **MTP/MPO**: Multi-fiber connectors for 40/100+ Gbps links

### Media Converters
Devices that allow different types of media to interconnect (e.g., copper to fiber). Useful in extending network distances or integrating older equipment.

- **Copper-to-Fiber**: Converts electrical signals to optical
- **Single-mode to Multi-mode**: Adapts fiber types
- **Bidirectional (BiDi)**: Uses a single fiber strand for TX/RX
- **Managed vs Unmanaged**: Managed converters offer SNMP/monitoring

## Cabling Tools
Essential tools for installing, testing, and maintaining network cables.

- **Crimpers**: Used to attach RJ45/RJ11 connectors to cable ends
- **Wire strippers**: Remove insulation from cables without damaging conductors
- **Punchdown tool**: Terminates wires into punchdown blocks (66/110)
- **Cable tester**: Verifies correct pinouts, continuity, and detects shorts
- **TDR (Time Domain Reflectometer)**: Tests copper cable length, detects breaks or shorts
- **OTDR (Optical Time Domain Reflectometer)**: Tests fiber length, loss, and faults

---

## Wired network standards
| Standard | Medium | Speed | Max Distance |
|----------|--------|-------|--------------|
| **10BASE-T** | Cat3 UTP | 10 Mb/s | 100 m |
| **100BASE-TX** | Cat5 UTP | 100 Mb/s | 100 m |
| **1000BASE-T** | Cat5e/6 UTP | 1 Gb/s | 100 m |
| **10GBASE-T** | Cat6a/7 UTP | 10 Gb/s | 100 m |
| **1000BASE-LX** | SMF | 1 Gb/s | 5 km |
| **10GBASE-SR** | MMF | 10 Gb/s | 300 m |

---


## WAN Technologies

### PSTN
- **Dial-up**: 56Kbps max (POTS)
- **ISDN**: Digital (128Kbps, BRI/PRI)
- **xDSL**: Digital Subscriber Line variants:
  - ADSL: Asymmetric (faster download)
  - VDSL: Very-high-bitrate (fiber hybrid)

### Broadband
- **DOCSIS**: Cable modem standard (3.1 = 10Gbps)
- **Fiber**:
  - FTTH: Fiber to Home
  - FTTC: Fiber to Curb
  - FTTN: Fiber to Node

### Wireless
- **Cellular**: 4G LTE, 5G (mmWave)
- **WiMAX**: IEEE 802.16 (alternative to DSL)
- **Satellite**: High latency (Geostationary/LEO)

### Enterprise WAN
- **Metro Ethernet**: Ethernet over MAN
- **Leased Lines**: T1 (1.544Mbps), E1 (2.048Mbps)
- **MPLS**: Label switching for QoS
- **Frame Relay**: Legacy packet-switched
- **ATM**: Fixed 53-byte cells (obsolete)

---

## Network Topologies
Describes how network devices are physically or logically arranged.

- **Peer-to-peer**: Devices communicate directly without central server
- **Client/server**: Centralized services with dedicated servers
- **Hybrid**: Mix of two or more topologies
- **Bus**: Single backbone with terminators at ends (legacy)
- **Ring**: Devices connected in circular fashion; one device failure can disrupt network
- **Star**: All devices connect to a central hub or switch
- **Mesh**: Devices interconnect with many redundant paths (full/partial)
- **Point-to-point**: Direct connection between two devices
- **Point-to-multipoint**: Central node communicates with multiple endpoints
- **MPLS**: Logical overlay that uses labels instead of IP routes for fast, efficient routing

## Network Infrastructure Implementations
Defines the scope and scale of network coverage.

- **PAN (Personal Area Network)**: Short-range (e.g., Bluetooth, USB tethering)
- **LAN (Local Area Network)**: Covers a single building or campus
- **MAN (Metropolitan Area Network)**: Spans a city or large campus
- **WAN (Wide Area Network)**: Covers large geographic areas (e.g., the Internet)
- **SCADA (Supervisory Control and Data Acquisition)**: Industrial control systems for monitoring and controlling infrastructure (e.g., power plants, water treatment)
- **Medianet**: Cisco term for networks optimized for media (e.g., video conferencing, streaming)

---

## Switches

Switches are Layer 2 (and sometimes Layer 3) devices that forward Ethernet frames based on MAC addresses. They are essential for connecting devices within a local area network (LAN) and creating efficient, collision-free communication paths.

### Unmanaged vs. managed switches

Unmanaged switches are plug-and-play and offer no configuration capabilities. They are typically used in small networks or home environments.

Managed switches provide features such as VLAN support, port mirroring, STP configuration, traffic monitoring, and SNMP integration. They are used in enterprise or complex networks where control and visibility are needed.

### Spanning tree protocol

Spanning Tree Protocol (STP) prevents loops in Layer 2 networks by detecting redundant paths and selectively blocking ports to maintain a loop-free topology. Enhanced versions like RSTP and MSTP provide faster convergence and multiple tree support.

### Switch port

A switch port is a physical interface that connects a device to the switch. Ports can be configured to behave differently:
- Access ports carry traffic for a single VLAN.
- Trunk ports carry traffic for multiple VLANs using tagging.
- Mirrored ports replicate traffic for monitoring or analysis.

### VLAN

A Virtual LAN (VLAN) logically segments a network into isolated domains, even if they share the same physical infrastructure. VLANs help improve security, manageability, and traffic isolation.

### Trunking

Trunking allows multiple VLANs to be transmitted over a single physical link between switches or between a switch and router. The IEEE 802.1Q standard is commonly used for tagging VLAN information in Ethernet frames.

### Port bonding

Port bonding, also known as link aggregation or EtherChannel, combines multiple physical interfaces into one logical link. This provides increased bandwidth and redundancy between devices.

### Power over Ethernet

Power over Ethernet (PoE) delivers both electrical power and data over a single Ethernet cable. It is commonly used for powering access points, IP phones, and surveillance cameras without needing separate power sources.

### Port mirroring

Port mirroring is used to duplicate the traffic from one or more switch ports to another port for monitoring or analysis. It is commonly used with intrusion detection systems or packet capture tools.


## WAN components
| Component | Purpose & Key Points |
|-----------|---------------------|
| **Copper line drivers / Repeaters** | Boost and reshape attenuated electrical signals on long copper runs (e.g., T-carriers, DSL) to extend distance and reduce bit errors. |
| **Demarc (Demarcation Point)** | Legally defined hand-off between customer-premises equipment (CPE) and the service-provider network; responsibility for troubleshooting changes here. |
| **Network Interface Unit (NIU)** | Basic telco hand-off device; presents RJ-11/RJ-45, offers surge protection, simple loopback testing. |
| **Smartjack** | Enhanced NIU that adds diagnostics such as remote loopback, performance LEDs, and signal conditioning; common on T1/E1 circuits. |
| **CSU/DSU** | Channel Service Unit/Data Service Unit; converts router serial signals to provider’s digital framing, supplies clocking, line coding, and loopback tests. |

---