---
title: "1.6_cloud_&_virtualization.net"
date: 2025-06-21T09:22:57-00:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---


## Virtualization

Virtualization is the process of creating a virtual version of physical hardware or resources, allowing multiple systems to run on a single physical machine. It improves hardware utilization, scalability, and flexibility in modern IT environments.

### Hypervisor
A hypervisor is software that creates and runs virtual machines (VMs). It abstracts physical hardware and enables multiple operating systems to run independently on the same physical host.

Types:
- **Type 1 (bare-metal)**: Runs directly on hardware (e.g., VMware ESXi, Microsoft Hyper-V, Xen).
- **Type 2 (hosted)**: Runs on top of a host OS (e.g., VirtualBox, VMware Workstation).

### Virtual machine manager
A virtual machine manager (VMM) is the component that manages the execution of virtual machines. It allocates resources, handles VM states (start, pause, snapshot), and interfaces with the hypervisor.

### Components of virtualization
- **Hypervisor**: Creates and manages virtual machines.
- **Guest OS**: Operating system installed inside the VM.
- **Virtual hardware**: Emulated components (CPU, RAM, NIC).
- **Management tools**: Interfaces for creating, monitoring, and configuring VMs.

### Software defined networking
Software-Defined Networking (SDN) decouples the control plane from the data plane in network devices. Instead of configuring hardware individually, SDN enables centralized management via software controllers.

Benefits:
- Centralized control
- Programmability
- Faster automation
- Improved scalability

---

## Storage area networks

Storage Area Networks (SANs) are high-speed networks that provide access to consolidated storage resources. SANs are commonly used in enterprise environments for block-level storage, enabling efficient data transfer between servers and storage devices.

Technologies:
- **Fibre Channel (FC)**
- **iSCSI**
- **FCoE (Fibre Channel over Ethernet)**

Advantages:
- High performance
- Centralized storage
- Better backup and disaster recovery options

---

## Cloud computing

Cloud computing delivers computing services (e.g., servers, storage, databases, networking) over the internet (“the cloud”). It allows for on-demand resources, flexible scaling, and reduced infrastructure costs.

### Classification of cloud computing
- **Deployment Models**:
  - **Public Cloud**: Shared infrastructure (e.g., AWS, Azure).
  - **Private Cloud**: Dedicated resources for one organization.
  - **Hybrid Cloud**: Combination of public and private environments.
- **Service Models**:
  - **IaaS (Infrastructure as a Service)**: Virtual machines, networks (e.g., AWS EC2).
  - **PaaS (Platform as a Service)**: Runtime environments for development (e.g., Heroku).
  - **SaaS (Software as a Service)**: End-user applications (e.g., Google Workspace, Office 365).

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