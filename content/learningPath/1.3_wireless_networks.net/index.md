---

title: "1.3_wireless_networks.net"
date: 2025-06-21T09:22:00-07:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*Wireless signals extend the network’s reach, transforming radio waves into seamless connectivity across offices, campuses, and cities.*

---

# 1  WLAN Infrastructure Overview

Wireless LANs replace the copper last‑drop with radio, yet still rely on familiar Ethernet switching and IP routing behind the access layer.

| Component                         | Role                                                | Notes                                             |
| --------------------------------- | --------------------------------------------------- | ------------------------------------------------- |
| **Access Point (AP)**             | 802.11 transceiver bridging RF ↔ wired LAN          | Split‑MAC (CAPWAP) or autonomous (local MAC)      |
| **Wireless LAN Controller (WLC)** | Centralised policy, RF management, seamless roaming | CAPWAP tunnels, dynamic channel/power (RRM)       |
| **Cloud‑Managed Platform**        | SaaS orchestration, zero‑touch provisioning         | Telemetry, AI‑driven RF optimisation              |
| **PoE Switch**                    | Powers APs (802.3at/bt)                             | Budget 30 W per Wi‑Fi 6 AP, 60 W for tri‑radio 6E |
| **RADIUS / LDAP**                 | 802.1X authentication backend                       | WPA2‑/WPA3‑Enterprise                             |

> **CAPWAP** (Control And Provisioning of Wireless Access Points) tunnels control messages over UDP 5246 and optionally data over UDP 5247.

---

# 2  Wi‑Fi (802.11) Standards Evolution

| Std      | Wi‑Fi Name   | Bands       | Max PHY\* | Channel Width    | Key Enhancements                   |
| -------- | ------------ | ----------- | --------- | ---------------- | ---------------------------------- |
| 802.11a  | —            | 5 GHz       | 54 Mb/s   | 20 MHz           | OFDM                               |
| 802.11b  | —            | 2.4 GHz     | 11 Mb/s   | 22 MHz           | DSSS                               |
| 802.11g  | —            | 2.4 GHz     | 54 Mb/s   | 20 MHz           | Back‑compat with b                 |
| 802.11n  | Wi‑Fi 4      | 2.4/5 GHz   | 600 Mb/s  | 20/40 MHz        | MIMO 4×4, HT                       |
| 802.11ac | Wi‑Fi 5      | 5 GHz       | 6.9 Gb/s  | 20/40/80/160 MHz | 256‑QAM, MU‑MIMO                   |
| 802.11ax | Wi‑Fi 6 / 6E | 2.4/5/6 GHz | 9.6 Gb/s  | 20‑160 MHz       | OFDMA, 1024‑QAM, TWT, BSS Color    |
| 802.11be | Wi‑Fi 7 †    | 2.4/5/6 GHz | 46 Gb/s   | 20‑320 MHz       | 4096‑QAM, Multi‑Link Ops, CMU‑MIMO |

\*PHY = physical‑layer data rate; real throughput ≈ 45–60 % after MAC/airtime overhead.
†Draft at time of writing.

---

# 3  RF & Channel Planning Basics

* **2.4 GHz** – 3 non‑overlapping 20 MHz channels (1, 6, 11). Longer range, higher interference.
* **5 GHz** – 24 non‑DFS 20 MHz channels; DFS spectrum adds 15 more (radar detection required). Supports channel bonding up to 160 MHz.
* **6 GHz (Wi‑Fi 6E)** – 59 channels (20 MHz) in FCC domain; entirely DFS‑free, ideal for high‑density uplinks.

> Plan adjacent APs on non‑overlapping channels, aiming for ‑65 dBm RSSI and ≥ 25 dB SNR at client locations.

Formula: **FSPL (dB) = 32.4 + 20 log₁₀ d(km) + 20 log₁₀ f(MHz)**

---

# 4  Antenna Technology

| Type                | Pattern                         | Typical Use                       |
| ------------------- | ------------------------------- | --------------------------------- |
| **Omnidirectional** | 360° azimuth, 30°–60° elevation | Indoor ceiling‑mount APs          |
| **Patch/Panel**     | 60°–90° beam                    | Stadium sectors, warehouse aisles |
| **Yagi / Dish**     | 10°–25° highly directional      | Bridging buildings, backhaul      |
| **Sector**          | 120°                            | Outdoor campus or WISP tower      |

*Gain (dBi)* ≈ directivity; doubling gain ↑ 3 dB halves beamwidth. **Polarisation diversity** & **MIMO** (spatial streams) boost resilience and throughput.

---

# 5  Authentication & Encryption

| Mode                | Cipher          | Auth Method             | Notes                                                        |
| ------------------- | --------------- | ----------------------- | ------------------------------------------------------------ |
| **Open + OWE**      | None / AES‑CCMP | None                    | Opportunistic Encryption (RFC 8110) replaces “open” hotspots |
| **WPA2‑Personal**   | AES‑CCMP        | Pre‑Shared Key          | Home/SMB; PSK‑based                                          |
| **WPA3‑Personal**   | AES‑CCMP‑128    | **SAE** (Dragonfly)     | Resistant to offline dictionary attacks                      |
| **WPA2‑Enterprise** | AES‑CCMP        | 802.1X (EAP‑TLS, PEAP)  | Requires RADIUS; per‑user creds                              |
| **WPA3‑Enterprise** | AES‑GCM‑256     | 802.1X (EAP‑TLS‑TLS1.3) | Mandatory PMF, 192‑bit suite                                 |

Pairwise Master Key (PMK) caching & **Fast BSS Transition** (802.11r) cut roam times to < 50 ms for VoIP.

---

# 6  Roaming & Radio Resource Management

* **802.11k** – Neighbor reports let clients pre‑scan candidate APs.
* **802.11v** – BSS Transition Management steers clients to better AP/channel.
* **802.11r** – Fast BSS Transition (FT) derives new PTK without full handshake.

Controllers compute **Radio Resource Management (RRM)**: dynamic channel/power, load‑balancing, band‑steering (push dual‑band clients to 5/6 GHz).

---

# 7  Wi‑Fi Frame Categories

| Category       | Examples                   | Purpose                          |
| -------------- | -------------------------- | -------------------------------- |
| **Management** | Beacon, Probe, Auth, Assoc | Establish & maintain connections |
| **Control**    | ACK, RTS/CTS, BlockAck     | Coordinate access to medium      |
| **Data**       | QoS Data, Null‑Data        | Carry user payload               |

Airtime fairness depends on MAC efficiency: fewer management frames, aggregate MSDUs (A‑MSDU) & MPDUs (A‑MPDU) to amortise overhead.

---

# 8  WLAN Topologies

## 8.1  Ad‑Hoc (IBSS)

Peer‑to‑peer without infrastructure; limited scale and no roaming.

## 8.2  Infrastructure (BSS/ESS)

Clients associate to AP(s) forming Basic Service Sets; multiple BSS under one SSID constitute an **ESS** enabling roaming.

## 8.3  Mesh (802.11s / Proprietary)

APs create wireless backhaul links; self‑healing; adds latency vs wired uplink.

---

# 9  Identifiers & Service Sets

| Term           | Definition                                               |
| -------------- | -------------------------------------------------------- |
| **SSID**       | Network name broadcast in Beacon; unicode up to 32 chars |
| **BSSID**      | Radio MAC (one per AP radio per WLAN)                    |
| **ESSID**      | Group of APs sharing SSID across an ESS                  |
| **RSSI / SNR** | Signal strength / quality; target ‑65 dBm, > 25 dB SNR   |

> Monitor **channel utilisation** (< 50 %) and **airtime** (client airtime fairness) using WLC or `iw`/`airodump‑ng` during surveys.
