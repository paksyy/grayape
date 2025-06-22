---
title: "1.5_network_operations.net"
date: 2025-06-21T09:22:35Z
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*A single operational playbook—monitoring, analysis, configuration, documentation, backups, forensics, and resilience—**all original text intact, only rearranged for clearer flow**.*

---

# 1  Monitoring & Visibility

## 1.1  Lightweight Real-Time Monitors
- **iftop** ![iftop](iftop.png)  
- **nethog** ![nethog](nethog.png)  
- **iptraf-ng** ![iptraf-ng](iptraf-ng.png)

## 1.2  Connectivity & Path Analysis

### ping  
ICMP reachability/RTT test. ![ping](ping.png)

### traceroute  
Lists hop-by-hop path and latency. ![traceroute](traceroute.png)

### ip  
Manages interfaces, IPs, routes, ARP tables. ![ip](ip.png)

### netcat  
Swiss-army knife for TCP/UDP diagnostics, file transfer, banner grabbing, reverse shells. ![netcat](netcat.png)

## 1.3  Enterprise-Scale Monitoring

### 1.3.1  Tool Arsenal
- **Nagios / Zabbix** – Host & service availability  
- **nmap** – Host/port/service discovery ![nmap](nmap.png)  
- **tcpdump** ![tcpdump](tcpdump.png)  
- **wireshark** ![wireshark](wireshark.png)

### 1.3.2  Log Sources
Firewall • DHCP • DNS • Router/Switch • Authentication logs  
*Reveal intrusions, misconfig, bottlenecks, failures.*

---

# 2  Configuration Management

Agentless & agent-based frameworks ensure consistency:

- **Ansible** • **Puppet** • **Chef** • **SaltStack**

**Benefits**: fewer errors • faster deployment • version control • compliance.

---

# 3  Network Documentation

Topology diagrams • IP allocations • Device inventory • Change logs • Access control matrices.  
*Accurate docs cut MTTR and onboarding time.*

---

# 4  Backup & Resilience

## 4.1  Backup Fundamentals
Full • Incremental • Differential

**What to back up**: Router/Switch configs • Servers/DBs • VMs • Firewall rules/ACLs  
**Storage**: On-site, Off-site, Cloud  
*Test restores regularly.*

## 4.2  Disaster & Continuity Planning
- **Disaster Recovery Plan** – Restore IT quickly after incident  
- **Business Continuity Plan** – Keep critical ops running during & after disaster  
- **Single Point of Failure (SPOF)** – Remove via clustering/redundancy  
- **UPS** – Graceful shutdown / generator transition  
- **First Responders** – Preserve evidence, contain, notify  
- **Data Breach** – Unauthorized data access; requires response/notification

---

# 5  Forensics & SIEM

Chain of custody • Disk imaging • Volatile vs non-volatile data • Hashing • Timeline analysis • Live forensics • Anti-forensics tactics.

---

