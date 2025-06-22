---
title: "1.6_cloud_&_virtualization.net"
date: 2025-06-21T09:22:57Z
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*A consolidated guide to virtualization, software-defined networking, storage area networks, and cloud-computing models—**all original text preserved and simply re-ordered into a clear chapter structure**.*

---

# 1  Virtualization Fundamentals

Virtualization creates virtual versions of hardware or resources so that multiple systems can run on a single physical machine—boosting utilization, scalability, and flexibility.

## 1.1  Hypervisors
Software that creates and runs VMs by abstracting physical hardware.

| Type | Runs On | Common Platforms |
|------|---------|------------------|
| **Type 1 (bare-metal)** | Direct on hardware | VMware ESXi, Microsoft Hyper-V, Xen |
| **Type 2 (hosted)**     | On top of a host OS | VirtualBox, VMware Workstation |

## 1.2  Virtual Machine Manager (VMM)
Component that manages VM execution—resource allocation, start/stop, snapshots—and interfaces with the hypervisor.

## 1.3  Core Components
- **Hypervisor** – Creates & manages VMs  
- **Guest OS** – OS running inside each VM  
- **Virtual hardware** – Emulated CPU, RAM, NIC, etc.  
- **Management tools** – GUIs/CLI/REST to provision & monitor VMs

## 1.4  Software-Defined Networking (SDN)
Decouples the control plane from the data plane, enabling centralized, programmable network management.

**Benefits**  
Centralized control • Programmability • Faster automation • Improved scalability

---

# 2  Storage Area Networks (SAN)

High-speed networks giving servers block-level access to pooled storage.

| Technology | Notes |
|------------|-------|
| **Fibre Channel (FC)** | Low-latency, high throughput |
| **iSCSI**             | SCSI over IP; leverages existing LAN |
| **FCoE**              | Fibre Channel frames over Ethernet |

**Advantages**  
High performance • Centralized storage • Better backup / DR

---

# 3  Cloud Computing

Delivery of compute, storage, DB, and networking over the Internet (“the cloud”) for on-demand scale and cost efficiency.

## 3.1  Deployment Models
- **Public Cloud** – Shared infra (AWS, Azure)  
- **Private Cloud** – Dedicated to one org  
- **Hybrid Cloud** – Mix of public & private

## 3.2  Service Models
| Model | What You Get | Example |
|-------|--------------|---------|
| **IaaS** | Virtual machines, networks | AWS EC2 |
| **PaaS** | Runtime / middleware | Heroku |
| **SaaS** | Finished applications | Google Workspace, Office 365 |

---
