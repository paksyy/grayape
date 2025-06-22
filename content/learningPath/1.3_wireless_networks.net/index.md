---
title: "1.3_wireless_networks.net"
date: 2025-06-21T09:22:24Z
draft: false
toc: false
images:
tags:
  - Computer Networks
---

# 1  WLAN Infrastructure Overview
Wireless LANs provide network access via radio waves rather than copper or fiber cabling. A typical infrastructure includes:

- **Access points (APs)**  
- **Wireless controllers / cloud management**  
- **Antennas** for coverage and performance

---

# 2  Wi-Fi (802.11) Standards

| Standard | Band(s) | Max Data Rate | Notes |
|----------|---------|--------------|-------|
| **802.11a** | 5 GHz | 54 Mb/s | OFDM |
| **802.11b** | 2.4 GHz | 11 Mb/s | DSSS |
| **802.11g** | 2.4 GHz | 54 Mb/s | Backward-compatible with **b** |
| **802.11n** | 2.4/5 GHz | 600 Mb/s | MIMO, HT channels |
| **802.11ac** | 5 GHz | 6.9 Gb/s | Wider channels, MU-MIMO |
| **802.11ax (Wi-Fi 6)** | 2.4/5/6 GHz | 9.6 Gb/s | OFDMA, TWT, BSS-coloring |

---

# 3  Antenna Technology

- **Omnidirectional** – radiates 360°, ideal for general coverage  
- **Directional** – focuses energy toward a target, good for point-to-point links  
- **MIMO (Multiple Input, Multiple Output)** – uses multiple antennas for higher throughput and reliability

---

# 4  Wireless Access Points

- Bridge wireless clients to the wired LAN  
- Support multiple **SSIDs**, VLAN tagging, WPA3 security  
- Enterprise APs can be standalone, controller-based, or cloud-managed

---

# 5  WLAN Topologies

## 5.1  Ad-Hoc
Devices communicate directly without an AP—temporary, no central control.

## 5.2  Infrastructure
Most common: clients connect through a central AP that forwards traffic to the wired LAN.

## 5.3  Mesh
Multiple APs interconnect wirelessly, forming a self-healing fabric; ideal for large areas and outdoor deployments.

---

# 6  Identifiers & Service Sets

| Term | Purpose |
|------|---------|
| **SSID** (Service Set Identifier) | Human-readable network name. One AP can broadcast multiple SSIDs mapped to different VLANs or policies. |
| **BSSID** (Basic Service Set Identifier) | MAC address of the AP’s radio interface; uniquely identifies each AP, even if SSID is shared. |

