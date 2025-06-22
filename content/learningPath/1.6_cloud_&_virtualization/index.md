---

title: "1.6_cloud_&_virtualization.net"
date: 2025-06-21T09:22:30-07:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*Abstracted compute, programmable fabric, and container agility let workloads float free of hardware confines.*

---
# 1  Virtualization Fundamentals

Virtualization abstracts hardware so that multiple isolated systems share one physical server—boosting utilization, elasticity, and disaster‑recovery options.

## 1.1  Hypervisors

Software that provisions and runs VMs by intercepting privileged CPU instructions and brokering access to memory, I/O and firmware.

| Type                    | Runs On             | Typical Platforms                                | Notes                                                |
| ----------------------- | ------------------- | ------------------------------------------------ | ---------------------------------------------------- |
| **Type 1 (bare‑metal)** | Direct on hardware  | VMware ESXi, Microsoft Hyper‑V, KVM, Xen         | Lowest latency; hardware passthrough (SR‑IOV, VT‑d). |
| **Type 2 (hosted)**     | Inside a desktop OS | VMware Workstation, Oracle VirtualBox, Parallels | Great for labs; relies on host OS drivers.           |

### Hardware Assist & Isolation

* **Intel VT‑x / AMD‑V** – Trap‑and‑emulate at ring ‑1.
* **Nested virtualization** – Run a hypervisor within a VM (useful for CI).
* **Paravirtual drivers (virtio)** – Bypass emulation overhead for NIC/disk.

> **Security pitfall:** Keep tools/guest‑additions patched—old drivers allow VM‑escape.

## 1.2  Virtual Machine Manager (VMM)

Controls lifecycle: clone, snapshot, hot‑add vCPU/RAM, vMotion/live‑migration, HA clustering. Modern VMMs expose REST/GraphQL APIs for IaC pipelines.

## 1.3  Core Components Revisited

* **Hypervisor** – Schedules vCPU, maps pages, emulates devices.
* **Guest OS** – Believes it owns bare metal; requests are trapped.
* **Virtual hardware** – Emulated BIOS/UEFI, NICs, GPU (vGPU/PCIe passthrough).
* **Mgmt tools** – vCenter, oVirt, OpenStack Nova; Terraform/Ansible providers.

## 1.4  Software‑Defined Networking (SDN)

The control plane (policy decisions) is separated from the data plane (packet forwarding).

| Layer           | Component                                            | Example                                     |
| --------------- | ---------------------------------------------------- | ------------------------------------------- |
| **Application** | Automation/orchestration                             | Ansible, Terraform, Kubernetes CNI          |
| **Control**     | Centralized controller                               | OpenDaylight, ONOS, Cisco ACI, VMware NSX‑T |
| **Data**        | Commodity switches w/ OpenFlow, P4, or VXLAN offload | White‑box ASICs, DPDK hosts                 |

Benefits → fast provisioning, intent‑based policy, micro‑segmentation, DR site stretch.

---

# 2  Storage Area Networks (SAN)

High‑speed block storage shared by hosts.

| Technology             | Throughput | Transport               | Key Concepts                             |
| ---------------------- | ---------- | ----------------------- | ---------------------------------------- |
| **Fibre Channel (FC)** | 8–128 Gb/s | FC fabric               | Zoning, WWPN masking, dual fabrics.      |
| **iSCSI**              | 1–100 Gb/s | IP/Ethernet             | IQN, LUN mapping, multipath I/O (MPIO).  |
| **FCoE**               | 10–40 Gb/s | Lossless Ethernet (DCB) | Combines LAN + SAN; VLAN / VSAN tagging. |

*Advantages:* Centralized storage, LAN‑free backup, thin provisioning, rapid snapshot/clone.

---

# 3  Cloud Computing Basics

Cloud providers pool compute, storage, and networking, delivering pay‑as‑you‑go resources via APIs and self‑service portals.

## 3.1  Deployment Models

| Model             | Description                  | Typical Use                        |
| ----------------- | ---------------------------- | ---------------------------------- |
| **Public Cloud**  | Shared infra (multi‑tenant)  | Start‑ups, variable workloads.     |
| **Private Cloud** | Dedicated (on‑prem/off‑prem) | Regulated data, latency‑sensitive. |
| **Hybrid Cloud**  | Federates public + private   | Gradual migration, burst capacity. |
| **Multi‑Cloud**   | Two+ public clouds           | Avoid lock‑in, geopolitical DR.    |

## 3.2  Service Models & Shared Responsibility

| Model    | Provider Manages                 | Customer Manages          |
| -------- | -------------------------------- | ------------------------- |
| **IaaS** | HW, hypervisor, basic networking | Guest OS, data, FW rules. |
| **PaaS** | Runtime, autoscale, DBaaS        | Code, access control.     |
| **SaaS** | Application & stack              | Data usage, entitlements. |

Security is *shared*—misconfig S3 bucket leaks are on you.

---

## 3.3  Cloud Networking Basics

Virtual private networks isolate tenant traffic.

| Concept                     | AWS                                         | Azure                 | Purpose                                                 |
| --------------------------- | ------------------------------------------- | --------------------- | ------------------------------------------------------- |
| **Virtual Network**         | VPC                                         | VNet                  | Private IP space /16–/28 CIDR.                          |
| **Subnets**                 | Subnet                                      | Subnet                | Layer‑3 isolation; route‑table attach.                  |
| **Security Controls**       | Security Group (stateful), NACL (stateless) | NSG, ASG              | Permit/deny at instance or subnet edge.                 |
| **Peering**                 | VPC Peering                                 | VNet Peering          | Private RFC 1918 links (no IGW).                        |
| **Transit Hub**             | Transit Gateway                             | Virtual WAN/Hub       | Full‑mesh via hub‑and‑spoke.                            |
| **Private Link / Endpoint** | Interface/ Gateway Endpoint                 | Private Link/Endpoint | Consume SaaS/API over provider backbone (no public IP). |

> **Attack surface:** Open 0.0.0.0/0 SG ingress, overly permissive IAM for TGW attachments, unused IPv6 blocks.

---

# 4  Containerization & Container Networking

Containers package processes with minimal OS libraries (cgroups, namespaces). Faster spin‑up than VMs; ideal for microservices.

## 4.1  Docker Network Drivers

| Driver               | Isolation Mechanism              | Use Case                      | Security Concern                            |
| -------------------- | -------------------------------- | ----------------------------- | ------------------------------------------- |
| **bridge** (default) | NATed veth pair + userland proxy | Single‑host dev               | Port‑mapping exposes 0.0.0.0 if not scoped. |
| **host**             | Shares host net‑ns               | High‑perf, low overhead       | No isolation; container can bind :22.       |
| **overlay**          | VXLAN w/ kv‑store (Swarm, K8s)   | Multi‑host clusters           | MTU/fragmentation, UDP 4789 flood.          |
| **macvlan/ipvlan**   | L2 passthrough w/ unique MAC/IP  | Legacy apps needing broadcast | Bypass host firewall; watch ARP spoof.      |
| **none**             | No NIC attached                  | Custom net‑ns experiments     | Accidental process isolation gap.           |

## 4.2  Kubernetes (CNI) & Policy

* **CNI plugins** – Calico, Flannel, Cilium (eBPF), Weave.
* **Service discovery** – kube‑proxy iptables/ipvs + CoreDNS.
* **NetworkPolicy** – Namespace/label‑based egress/ingress filters; enforce least privilege.

### Breakout & Defense

| Misconfig                            | Exploit                                 | Mitigation                              |
| ------------------------------------ | --------------------------------------- | --------------------------------------- |
| Privileged container + host net‑ns   | Ping gateway, ARP spoof peers           | Deny `privileged`, `hostNetwork: true`. |
| Wildcard port‑map `-p 0.0.0.0:80:80` | External attacker hits internal service | Restrict to `127.0.0.1` or LB IP.       |
| cgroup `net_cls` leak                | Bypass egress shaping                   | Use seccomp & AppArmor profiles.        |
