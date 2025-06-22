---

title: "1.7_politics_&_compliances.net"
date: 2025-06-21T09:23:30-07:00
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*Policies, audits, and standards translate technical safeguards into enterprise-wide accountability.*

---
# 1  Corporate Policy Framework

## 1.1  Bring‑Your‑Own‑Device (BYOD) Policy

A BYOD policy governs how employees can use personal devices (phones, laptops, tablets) to access corporate networks and data.

### Security Considerations

* Enforce strong authentication (e.g., MFA)
* Require full‑disk and mobile storage encryption
* Use mobile‑device management (**MDM**)
* Restrict access based on role, network zone, or geolocation
* Monitor for malicious or non‑compliant behaviour

### Benefits

* Increased flexibility and user satisfaction
* Reduced hardware costs

### Risks

* Data leakage
* Malware introduction
* Non‑compliant endpoints

---

## 1.2  Acceptable‑Use & Remote‑Work Policies

Supplemental to BYOD, these policies define approved software, prohibited activities (pirated media, offensive content, personal cloud drives), and minimum workstation hardening (screen‑lock ≤ 10 min, corporate VPN, OS auto‑patch) for employees connecting from home or shared spaces.

---

# 2  Network Governance Controls

## 2.1  Network Segmentation

Dividing a network into smaller subnetworks (segments) to improve performance and security.

### Types

* **Physical segmentation** – Separate hardware (e.g., dedicated switches)
* **Logical segmentation** – VLANs, ACLs, VRF‑Lite, micro‑segmentation firewalls

### Benefits

* Limits lateral movement of attackers
* Enables role‑based access control
* Contains malware/breaches in isolated segments
* Improves broadcast & multicast performance

### Common Segments

* User LAN
* Server VLAN / DMZ
* Management network (OOB)
* Guest Wi‑Fi
* IoT/OT devices
* Build/CI runners
* Backup & storage fabric

> Segmentation is a cornerstone of **zero‑trust architectures** and layered defense‑in‑depth strategies.

## 2.2  Network Access Control (NAC) & Zero‑Trust

* **802.1X** authenticates devices before DHCP.
* NAC posture checks (AV, patch level) determine VLAN assignment.
* Micro‑segmentation enforces identity‑aware policy at every hop.

---

# 3  Logging, Monitoring & Retention

Understanding where your breadcrumbs are stored (and for how long) is as important to defenders as it is to red‑teamers who wish to cover—or plant—tracks.

## 3.1  Core Log Repositories

| Source                    | Typical Storage                                          | Key Artifacts                             |
| ------------------------- | -------------------------------------------------------- | ----------------------------------------- |
| **Syslog / RSyslog**      | Central syslog server, SIEM                              | Auth, daemon, kernel, cron events         |
| **NetFlow / IPFIX**       | Flow collector (nfdump, Kentik)                          | 5‑tuple + byte/packet counts              |
| **Firewall & IDS**        | Device local + syslog                                    | Connection allowed/denied, signatures hit |
| **Endpoint EDR**          | Vendor cloud, on‑prem data‑lake                          | Process start, registry, telemetry        |
| **Cloud Audit**           | AWS CloudTrail, Azure Activity Log, GCP Cloud Audit Logs | API calls, IAM changes, console logins    |
| **Object Storage Access** | S3 Server‑Access Logs, Azure Storage Logs                | Read/Write ops, source IP, auth type      |

## 3.2  Retention & Compliance Matrix

| Log Family              | Baseline Retention | Regulations Impacted         | Storage Tactic                     |
| ----------------------- | ------------------ | ---------------------------- | ---------------------------------- |
| Authentication & IAM    | 1–7 years          | SOX, ISO 27001, PCI DSS      | WORM S3/Glacier, compressed syslog |
| Network Flow & Security | 90 days – 1 year   | NIST 800‑171, HIPAA          | Hot storage SIEM, cold object tier |
| Application & DB        | 30–90 days         | GDPR (data subject requests) | Indexed in Elastic, archived to S3 |
| Cloud Control‑Plane     | ≥1 year            | CIS Benchmarks, FedRAMP      | Cloud provider immutable store     |

### Tamper‑Resistance

* **TLS syslog** or **Secure Copy** to off‑box store
* Immutable storage (S3 Object‑Lock, WORM Blu‑ray)
* Hash chain or blockchain‑anchored log proofs
* Least‑privilege on SIEM delete APIs

## 3.3  Red‑Team Perspective

Knowing log paths allows:

* **Log poisoning** – Inject benign events to bury signals.
* **Log truncation** – Disable or rotate to force overwrite.
* **Selective deletion** – Remove only incriminating entries (requires high privilege and audit‑log parity checks).
  *Blue tip:* Enable alerts when verbose logging suddenly drops or file sizes reset.

---

# 4  Regulatory & Standards Mapping

| Framework                    | Focus                            | Key Requirements                                              |
| ---------------------------- | -------------------------------- | ------------------------------------------------------------- |
| **ISO 27001**                | ISMS                             | Risk assessment, asset inventory, continuous improvement      |
| **NIST SP 800‑53 / 800‑171** | US Federal / contractor controls | 17 control families incl. AC, AU, SC, CM                      |
| **GDPR**                     | EU privacy                       | Lawful basis, data‑subject rights, breach notification ≤ 72 h |
| **HIPAA**                    | US healthcare                    | PHI safeguards, audit trails, BAA contracts                   |
| **PCI DSS 4.0**              | Payment card data                | Segmentation, FIM, 12‑month log retention                     |
| **SOC 2**                    | Trust principles                 | Security, availability, confidentiality, processing integrity |

> **Tip:** Map technical controls (NAC, log retention, segmentation) directly to compliance clauses to avoid duplicate audit evidence.

---

# 5  Policy Lifecycle & Enforcement

1. **Draft** – Policy owner, scope, rationale.
2. **Review** – Legal, HR, Security, key business units.
3. **Approve** – C‑suite or steering committee sign‑off.
4. **Publish** – Intranet, onboarding decks, mandatory training.
5. **Enforce** – Technical controls (MDM, NAC), HR sanctions.
6. **Audit** – Annual internal + external audits; metrics (incident count, non‑compliant endpoints).
7. **Revise** – Reflect tech changes, new regs, incident findings.