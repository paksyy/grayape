---

title: "1.1_network_infrastructure.net"
date: 2025-06-21T09:21:00-07:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*Routers, switches, cables, and power systems form the physical highway that moves every bit from point A to point B—laying the foundation for all higher-layer services.*

---
# 1  Network Devices

## 1.1  Layer 1 Devices

* **Analog modem**: Developed to create connections between network segments via PSTN using POTS. Provides single connection (56 Kbps max).
* **Repeater / Regenerator**: Regenerates and reshapes a weakened signal to extend copper or fiber runs.
* **Transceiver** (*media‑dependent adapter*): Converts a NIC’s signaling to the medium in use (e.g., 10BASE‑T MAU, 1000BASE‑SX optical module).
* **Hub**: Multi‑port repeater that operates half‑duplex and forms a single collision domain. Largely obsolete.

## 1.2  Layer 2 Devices

* **Bridge**: Early two‑port switch that forwards frames based on a MAC address table.
* **Switch**: Uses ASICs to learn MAC addresses and forward frames intelligently; creates a separate collision domain per port.
* **Wireless Access Point (WAP)**: Bridges wireless and wired networks; implements 802.11 standards (Wi‑Fi 6/6E).

## 1.3  Layer 3 Devices

* **Router**: Connects dissimilar networks using logical addressing; maintains routing tables (static/dynamic).
* **Multilayer Switch (MLS)**: Combines Layer 2 switching with wire‑speed Layer 3 routing features; common in campus cores.

## 1.4  Optimisation / Specialty Devices

* **Load Balancer**: Distributes traffic among servers (Round‑Robin, Least‑Connections, etc.).
* **Proxy Server**: Intermediary that makes requests on behalf of clients (forward/reverse, caching, content filtering).
* **Network TAP**: Passive inline device that copies traffic for monitoring/IDS without introducing latency.

## 1.5  Modular Interfaces & Transceiver Form‑Factors

| Form‑Factor        | Typical Speed      | Medium          | Notes                                                |
| ------------------ | ------------------ | --------------- | ---------------------------------------------------- |
| **GBIC**           | 1 Gb/s             | SX, LX, copper  | Legacy, large footprint                              |
| **SFP**            | 1 Gb/s             | SX, LX, copper  | “Mini‑GBIC”, hot‑swappable                           |
| **SFP+**           | 10 Gb/s            | SR, LR, DAC     | Backwards‑compatible with SFP slots in some switches |
| **QSFP+ / QSFP28** | 40 Gb/s / 100 Gb/s | SR4, LR4, DAC   | Four‑lane transceivers; break‑out to 4× SFP+         |
| **OSFP / QSFP‑DD** | 400 Gb/s           | SR8, DR4, FR4   | Next‑gen DC fabrics                                  |
| **DAC / AOC**      | 10–400 Gb/s        | Twin‑ax / Fiber | Low‑cost short‑reach links (≤ 7 m)                   |

*Tip ▸ Many ToR switches accept both SFP+/SFP28 and QSFP+/QSFP28, enabling flexible up‑/down‑links without forklift upgrades.*

---

# 2  Cabling & Media

## 2.1  Twisted‑Pair Cabling

* **UTP** – Unshielded (Cat 5/6/6a/8)
* **STP** – Shielded (industrial/noisy sites)
* **Plenum** – Low‑smoke jacket for HVAC spaces
* **Cable Types**:

  * **Straight‑through** – unlike devices (host ↔ switch)
  * **Crossover** – like devices (switch ↔ switch when Auto‑MDIX absent)
  * **Rollover** – Flat console cable (Cisco pinout)

### 2.1.1  Connectors & Pinouts

* **RJ11** – 6P2C, POTS/ADSL
* **RJ45** – 8P8C, Ethernet (T568A/B wiring)
* **66/110 Block** – Punch‑down cross‑connects
* **DB‑9/25** – Legacy serial/console

> **T568A vs T568B** ▸ Both use straight pin‑to‑pin mapping; only pair order differs. Mixing standards causes split pairs and crosstalk.

### 2.1.2  Categories (Copper)

| Category   | Bandwidth | Max Data Rate | Reach                              |
| ---------- | --------- | ------------- | ---------------------------------- |
| **Cat 5**  | 100 MHz   | 100 Mb/s      | 100 m (obsolete)                   |
| **Cat 5e** | 100 MHz   | 1 Gb/s        | 100 m                              |
| **Cat 6**  | 250 MHz   | 10 Gb/s       | 55 m                               |
| **Cat 6a** | 500 MHz   | 10 Gb/s       | 100 m                              |
| **Cat 7**  | 600 MHz   | 10 Gb/s       | 100 m; GG‑45/ARJ45 connector       |
| **Cat 8**  | 2 GHz     | 25/40 Gb/s    | 30 m; data‑center switch‑to‑server |

---

## 2.2  Coaxial Cabling

* **Impedance**: 75 Ω (video/broadband) vs 50 Ω (RF/data)
* **Shielded Core**: Central copper conductor + dielectric + metallic shield
* **Use Cases**: Cable TV, DOCSIS Internet, CCTV, amateur radio

### 2.2.1  Cable Types

* **RG‑6** – Modern CATV; thicker, low loss
* **RG‑59** – Legacy CCTV; higher attenuation
* **RG‑11** – Long‑haul drops; stiff

### 2.2.2  Connectors

* **BNC** • **F‑type** • **N‑type** – Weather‑sealed RF connector (50 Ω)

---

## 2.3  Fiber‑Optic Cabling

* **Core**: Glass or plastic; transmits photons instead of electrons
* **Use Cases**: Campus backbones, MAN rings, DWDM long‑haul

### 2.3.1  Cable Types

* **Single‑mode (SMF)** – 9 µm core, laser light, ≥ 100 km
* **Multi‑mode (MMF)** – 50/62.5 µm core, LED/VCSEL, ≤ 2 km

### 2.3.2  Fiber Classes & Colours

| Classification           | Jacket Colour | Reach (10 Gb/s)          |
| ------------------------ | ------------- | ------------------------ |
| **OM1** 62.5 µm          | Orange        | 33 m                     |
| **OM2** 50 µm            | Orange        | 82 m                     |
| **OM3** Laser‑optimised  | Aqua          | 300 m                    |
| **OM4** High‑bandwidth   | Aqua/Purple   | 400 m                    |
| **OM5** Wide‑band (SWDM) | Lime Green    | 400 m (WDM)              |
| **OS1/OS2** SMF          | Yellow        | > 10 km (λ 1310/1550 nm) |

### 2.3.3  Connector Types

LC • SC • ST • MTP/MPO (12/24‑fiber ribbon)

### 2.3.4  WDM (Wavelength‑Division Multiplexing)

CWDM (18 λ, 20 nm spacing) • DWDM (dense 0.8/0.4 nm) extends SMF capacity to multi‑terabit backbones.

---

## 2.4  Media Converters

Copper↔Fiber • SMF↔MMF • BiDi single‑strand • Managed (SNMP, DDM) vs unmanaged.

## 2.5  Cabling Tools

Crimpers • Punch‑down • Wiremap tester • Tone & Probe • TDR/OTDR • Fiber inspection scope

## 2.6  Wired‑Ethernet Standards (Common Selection)

| Standard                  | Medium       | Speed      | Reach |
| ------------------------- | ------------ | ---------- | ----- |
| **10BASE‑T**              | Cat 3 UTP    | 10 Mb/s    | 100 m |
| **100BASE‑TX**            | Cat 5 UTP    | 100 Mb/s   | 100 m |
| **1000BASE‑T**            | Cat 5e/6 UTP | 1 Gb/s     | 100 m |
| **2.5GBASE‑T / 5GBASE‑T** | Cat 5e/6     | 2.5/5 Gb/s | 100 m |
| **10GBASE‑T**             | Cat 6a/7     | 10 Gb/s    | 100 m |
| **10GBASE‑SR**            | MMF (OM3)    | 10 Gb/s    | 300 m |
| **10GBASE‑LR**            | SMF          | 10 Gb/s    | 10 km |
| **40GBASE‑SR4**           | MMF (MPO)    | 40 Gb/s    | 150 m |
| **100GBASE‑LR4**          | SMF          | 100 Gb/s   | 10 km |

---

# 3  WAN Technologies

## 3  WAN Technologies

Wide‑area networking links sites that are separated by kilometres—or continents—using copper, fibre, microwave, or satellite media. The choice of access technology affects speed, latency, cost, redundancy, and where the service‑provider demarcation lies.

### 3.1  PSTN / Copper Last‑Mile

| Variant                          | Medium              | Typical Throughput   | Distance | Notes                                                    |
| -------------------------------- | ------------------- | -------------------- | -------- | -------------------------------------------------------- |
| **Dial‑up (V.92)**               | Twisted pair (POTS) | 56 kb/s              | < 18 km  | Uses analog modulation; legacy out‑of‑band access.       |
| **ISDN BRI (2B + D)**            | Twisted pair        | 128 kb/s             | < 5 km   | Digital end‑to‑end; fast call setup.                     |
| **ISDN PRI (23B + D / 30B + D)** | T1/E1               | 1.544 / 2.048 Mb/s   | —        | Popular PBX trunking.                                    |
| **ADSL2+**                       | Twisted pair        | 24 Mb/s ↓ / 1 Mb/s ↑ | ≤ 5 km   | Asymmetric; PPPoE to DSLAM at CO.                        |
| **VDSL2 / Super‑Vectoring**      | Twisted pair        | 100–300 Mb/s ↓       | ≤ 1 km   | Delivered as FTTN/C; spectral bundling fights crosstalk. |

### 3.2  Broadband Fibre & Cable

* **DOCSIS 3.1** – Orthogonal‑FDM channels on hybrid‑fiber‑coax; up to 10 Gb/s downstream, 1–2 Gb/s upstream.
* **GPON / XGS‑PON** – Passive optical splitters (1:32/1:64) from OLT to ONUs; 2.5 Gb/s ↓ / 1.25 Gb/s ↑ (GPON) and 10 Gb/s symmetrical (XGS‑PON).
* **FTTx Variants**

  * **FTTH** – Fibre into the premises; no copper bottleneck.
  * **FTTC / FTTN** – Fibre to curb/node then VDSL over copper; cheaper roll‑out, speed limited by last‑mile copper.

### 3.3  Wireless WAN

| Technology          | Spectrum           | Data‑Rate          | Latency  | Use Cases                                          |
| ------------------- | ------------------ | ------------------ | -------- | -------------------------------------------------- |
| **4G LTE**          | 700 MHz–2.6 GHz    | 100–300 Mb/s       | 40–60 ms | Primary or fail‑over branch links.                 |
| **5G NR**           | sub‑6 GHz / mmWave | 1–10 Gb/s (mmWave) | 10–20 ms | High‑density urban back‑haul; low‑lat IoT.         |
| **WiMAX (802.16e)** | 2.3/2.5/3.5 GHz    | ≤ 70 Mb/s          | 50–70 ms | Rural fixed wireless; eclipsed by LTE.             |
| **Satellite GEO**   | Ku/Ka‑band         | 25–100 Mb/s        | > 600 ms | Remote maritime, mining, desert.                   |
| **Satellite LEO**   | Ka‑band            | 100–350 Mb/s       | 25–50 ms | Mobile clinics, disaster relief, off‑grid offices. |

### 3.4  Enterprise‑Grade WAN Services

* **Leased Line / T‑Carrier / E‑Carrier** – Dedicated, symmetrical, point‑to‑point circuits; predictable latency and SLAs, but expensive at high speeds.
* **Metro Ethernet** – Provider MAN rings delivering E‑Line / E‑LAN services over fibre; presented as Ethernet NNI hand‑off with VLAN or QinQ.
* **MPLS L3VPN** – Label‑switched core providing any‑to‑any IP reachability plus QoS and traffic engineering; backbone for VoIP and ERP.
* **SD‑WAN** – Overlay of encrypted tunnels (often IPsec) steered across multiple underlays (broadband, LTE, MPLS) with central orchestration, policy‑based routing, and application‑aware path selection.

### 3.5  WAN Edge Components

| Device                          | Function                                                                          |
| ------------------------------- | --------------------------------------------------------------------------------- |
| **Smartjack / NIU**             | Telco demarc; provides loopback, alarms, lightning protection.                    |
| **CSU/DSU**                     | Line‑coding and clocking for T‑carrier; presents serial or RJ‑48 to router.       |
| **DSLAM**                       | Aggregates hundreds of xDSL circuits onto fibre uplinks at CO or street cabinet.  |
| **OLT (Optical Line Terminal)** | Provider head‑end for PON; splits downstream optical power to multiple ONUs.      |
| **Customer Edge (CE) Router**   | Runs BGP/OSPF/EIGRP toward provider PE; applies QoS marking and VRF segmentation. |

> **Note:** Bandwidth is useful only if latency and jitter meet the application’s needs—especially for voice, video, and transactional workloads.

## 4  Topologies & Scope.1  Physical & Logical Topologies

Bus • Ring • Star • Mesh • Tree • Point‑to‑Point • Point‑to‑Multipoint • Hybrid • **Overlay (MPLS, VXLAN)**

## 4.2  Network Scopes

PAN • LAN • CAN (Campus) • MAN • WAN • SCADA/ICS • Medianet

---

# 5  Switching Concepts

Switches interconnect hosts within a broadcast domain, learn **MAC addresses**, enforce segmentation with **VLANs**, and—on multilayer models—route IP traffic at wire speed. Modern campus fabrics add QoS, security controls, virtualization, and telemetry that blur traditional OSI‐layer boundaries.

---

## 5.1  MAC Learning & Forwarding

1. **Learning** – On ingress, the switch records the source MAC and the port in its **CAM** (Content‑Addressable Memory) table.
2. **Forward/Filter** – If the destination MAC is known, the frame is forwarded out the single egress port; otherwise it is **flooded** to all ports in the same VLAN (unknown‑unicast) along with broadcasts & multicasts.
3. **Aging** – Idle MAC entries time‑out (default = 300 s) to adapt to topology changes.

> *show mac address‑table* reveals learned entries; *clear mac‑address‑table* forces re‑learning—handy for troubleshooting duplicate IPs.

---

## 5.2  Unmanaged vs Managed

| Feature                 | Unmanaged                  | Managed                 |
| ----------------------- | -------------------------- | ----------------------- |
| VLANs                   | ✘                          | ✔                       |
| CLI/API/SNMP            | ✘                          | ✔                       |
| STP                     | ✘                          | ✔                       |
| QoS                     | Basic (802.1p passthrough) | Granular (DSCP/queuing) |
| Redundancy (LACP, VRRP) | ✘                          | ✔                       |
| PoE budgeting           | ✘                          | ✔                       |

Small/home switches stay cheap by omitting ASICs for TCAM (ACLs/QoS) and control‑plane CPUs.

---

## 5.3  Spanning‑Tree Deep Dive

* **Root Election** – Lowest **bridge ID** (priority + MAC) wins root; tune root by lowering priority (e.g., *spanning‑tree vlan 10 priority 4096*).
* **Port Roles** – Root Port (best path to root), Designated Port (best on segment), Alternate/Backup (blocked for redundancy).
* **Port States** – Blocking → Listening → Learning → Forwarding → Disabled.
* **Protection Features**:

  * **PortFast** – Skip Listening/Learning on access ports (faster DHCP).
  * **BPDU Guard** – Err‑disables a PortFast interface that receives BPDUs (rogue switch).
  * **Root Guard** – Prevents better bridge IDs from hijacking root.
  * **Loop Guard** – Blocks port if BPDUs suddenly stop (unidirectional link).
* **RSTP (802.1w)** converges in \~1 s by exchanging proposal/agree messages; **MSTP (802.1s)** maps multiple VLANs to a few spanning‑tree instances to shrink CPU load.

---

## 5.4  Switch Port Modes

| Mode              | VLAN Handling                              | Common Use                        |
| ----------------- | ------------------------------------------ | --------------------------------- |
| **Access**        | Untagged; single VLAN                      | End‑host PCs, printers            |
| **Voice Access**  | Untagged data VLAN + tagged voice VLAN     | IP phones with integrated PC port |
| **Trunk**         | Tagged frames (802.1Q); carries many VLANs | Switch uplinks, hypervisors       |
| **Hybrid**        | Mix of tagged + untagged                   | ISP hand‑offs, CCTV NVRs          |
| **Tunnel (QinQ)** | Outer tag preserves inner customer tags    | Carrier Metro‑Ethernet            |

DTP (Dynamic Trunking Protocol) auto‑negotiates access/trunk on Cisco; disable with *switchport nonegotiate* to avoid spoofing.

---

## 5.5  VLAN Architecture

*VLAN ≠ subnet*, but each subnet typically maps 1:1 to a VLAN for clarity.

* **Default VLAN 1** – Keep control‑plane traffic isolated; move user ports to other VLANs.
* **Private VLAN (PVLAN)** – Secondary Isolated/Community ports share a primary VLAN but cannot talk directly—great for DMZ hosting.
* **Voice VLAN** – Switch instructs LLDP‑MED/CDP phones which VLAN to tag; PC traffic remains untagged.
* **QinQ (802.1ad)** – “Carrier tag” + customer tag expands VLAN space to 4096² (\~16 M).

---

## 5.6  Trunking & Encapsulation

* **802.1Q** inserts a 4‑byte tag after the source MAC; includes 12‑bit VLAN ID and 3‑bit **CoS** field for Layer‑2 QoS.
* **Native VLAN** egresses untagged on a trunk; mis‑configurations lead to VLAN hopping attacks—set unused native VLAN or tag all VLANs (*vlan dot1q tag native*).
* **ISL** legacy Cisco proprietary trunking (< 1 G) now obsolete.

---

## 5.7  Link Aggregation (LAG)

* **Static EtherChannel** – Manual bundle; simple but mis‑match risk.
* **LACP (802.1AX)** – Negotiated bundle, detects mis‑wired links; *fast* (1 s) vs *normal* (30 s) timers.
* **Load‑Balancing** – Src/Dst MAC, Src/Dst IP, or L4 port hashed to select member link—beware polarization with hash symmetry.
* **MLAG / vPC** – Two chassis present a single LACP system‑ID—east/west control messages keep forwarding consistent.

---

## 5.8  Port‑Level Security & Storm Control

* **Port Security** – Limits number of learned MACs (1 for printers), violation actions: protect / restrict / shutdown.
* **Storm Control** – Drops broadcast/multicast/unknown unicast once a threshold (% of bandwidth) is exceeded—mitigates loops and DoS.
* **DHCP Snooping** – Builds a binding table of MAC→IP→port; feeds **Dynamic ARP Inspection** and **IP Source Guard** to block spoofing.

---

## 5.9  Quality of Service (QoS)

1. **Trust Boundary** – Where CoS/DSCP values become reliable (usually at the access switch facing an IP phone).
2. **Classification & Marking** – ACLs/NBAR inspect traffic, set DSCP.
3. **Queuing & Scheduling** – Strict‑priority for voice, weighted fair‑queue for data.
4. **Policing/Shaping** – Drop or buffer to enforce contract.

> Voice generally uses DSCP 46 (EF); video DSCP 34 (AF41); scavenger traffic DSCP 8 (CS1).

---

## 5.10  Power over Ethernet (PoE)

| Standard                  | Mode   | Power per Port          | Typical Devices                  |
| ------------------------- | ------ | ----------------------- | -------------------------------- |
| **802.3af (Type 1)**      | A/B    | 15.4 W (12.95 W usable) | VoIP phones, basic APs           |
| **802.3at (Type 2 PoE+)** | A/B    | 30 W                    | Dual‑band APs, PTZ cameras       |
| **802.3bt (Type 3)**      | 4‑pair | 60 W                    | Wi‑Fi 6 APs, thin clients        |
| **802.3bt (Type 4)**      | 4‑pair | 90 W                    | Pan‑tilt‑zoom cams, LED lighting |

Switches allocate a **power budget**; LLDP‑MED negotiates actual draw, enabling dynamic redistribution.

---

## 5.11  Traffic Monitoring

* **SPAN / RSPAN / ERSPAN** – Software mirroring within chassis, across VLAN, or IP GRE tunnel.
* **TAP** – Passive optical/electrical split, zero loss/latency—best for compliance captures.

---

## 5.12  Forwarding Architectures

* **Store‑and‑Forward** – Full‑frame CRC check; enables QoS/classification on ingress.
* **Cut‑Through** – Sub‑μs latency for HFT markets; corrupt frames propagate.
* **Fragment‑Free** – Waits first 64 bytes (Ethernet collision window) to filter runts.

---

## 5.13  Switch Fabric & Virtualisation

* **Cross‑bar / Clos Fabric** – Non‑blocking multi‑stage topology in modern DC spines.
* **Backplane Bandwidth** – Sum of switching ASIC busses; advertised as full‑duplex Gbit/s.
* **Stacking (ISSU/VSS/StackWise)** – Multiple switches act as one control‑plane; single management IP, rapid fail‑over.
* **In‑Service Software Upgrade (ISSU)** – Redundant supervisor modules allow hit‑less firmware patching.
