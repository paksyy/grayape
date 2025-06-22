---
title: "1.3_wireless_networks.net"
date: 2025-06-21T09:22:24-00:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

## WLAN infrastructure

Wireless LAN infrastructure enables network access using radio waves instead of physical cabling. It includes access points, wireless controllers, and antennas to provide reliable wireless coverage and performance.

### Wireless Access Standards

Wi-Fi standards define capabilities like frequency, speed, and channel width:
- 802.11a: 5 GHz, up to 54 Mbps
- 802.11b/g: 2.4 GHz, up to 11/54 Mbps
- 802.11n: 2.4/5 GHz, up to 600 Mbps with MIMO
- 802.11ac: 5 GHz, up to 1 Gbps with MU-MIMO
- 802.11ax (Wi-Fi 6): High efficiency, works on both 2.4 and 5 GHz

### Antenna technology

Antenna types influence coverage and direction:
- Omnidirectional antennas radiate in all directions, ideal for general coverage.
- Directional antennas focus the signal in a specific direction, useful for point-to-point links.
- MIMO (Multiple Input, Multiple Output) improves speed and reliability using multiple antennas.

### Wireless Access Points

Access points (APs) bridge wireless clients to the wired LAN. They support multiple SSIDs, VLAN tagging, and security features like WPA3. Enterprise APs can be managed individually or via a central controller or cloud platform.

---

## WLAN topologies

### Ad hoc topology

In an ad hoc topology, devices communicate directly with one another without an access point. This setup is temporary and lacks central control or scalability.

### Infrastructure topology

The most common WLAN topology. Devices connect to the network through a central access point, which manages traffic and connects to the wired LAN.

### Mesh topology

In mesh networks, multiple APs connect to each other wirelessly, forming a resilient and self-healing network. If one node fails, traffic reroutes through others. Common in large areas or outdoor deployments.

### SSID

The Service Set Identifier (SSID) is the name of the wireless network broadcasted by an access point. Clients use the SSID to identify and join the correct network. A single AP can broadcast multiple SSIDs, each mapped to a different VLAN or policy group.

### BSSID

The Basic Service Set Identifier (BSSID) is the MAC address of the radio interface on the access point. While the SSID is the network name seen by users, the BSSID uniquely identifies each AP or radio. This helps differentiate between access points broadcasting the same SSID.

## Wireless network standards
| Standard | Band(s) | Max Data Rate | Notes |
|----------|---------|--------------|-------|
| **802.11a** | 5 GHz | 54 Mb/s | OFDM |
| **802.11b** | 2.4 GHz | 11 Mb/s | DSSS |
| **802.11g** | 2.4 GHz | 54 Mb/s | Backward-compatible with b |
| **802.11n** | 2.4/5 GHz | 600 Mb/s | MIMO, HT |
| **802.11ac** | 5 GHz | 6.9 Gb/s | Wider channels, MU-MIMO |
| **802.11ax (Wi-Fi 6)** | 2.4/5/6 GHz | 9.6 Gb/s | OFDMA, TWT, BSS coloring |
