---
title: "1.7_politics_&_compliances.net"
date: 2025-06-21T09:22:57Z
draft: false
toc: false
images:
tags:
  - Computer Networks
---

*High-level governance topics—device‐use policy and segmentation controls—that underpin security compliance across modern enterprises. **All original wording kept; only the structure has been clarified.***

---

# 1  Corporate Policy Framework

## 1.1  Bring-Your-Own-Device (BYOD) Policy
A BYOD policy governs how employees can use personal devices (phones, laptops, tablets) to access corporate networks and data.

### Security Considerations
- Enforce strong authentication (e.g., MFA)  
- Require device encryption  
- Use mobile-device management (**MDM**)  
- Restrict access based on role or location  
- Monitor for malicious or non-compliant behavior  

### Benefits
- Increased flexibility and user satisfaction  
- Reduced hardware costs  

### Risks
- Data leakage  
- Malware introduction  
- Non-compliant endpoints  

---

# 2  Network Governance Controls

## 2.1  Network Segmentation
Dividing a network into smaller subnetworks (segments) to improve performance and security.

### Types
- **Physical segmentation** – Separate hardware (e.g., dedicated switches)  
- **Logical segmentation** – VLANs, ACLs, firewalls to steer traffic  

### Benefits
- Limits lateral movement of attackers  
- Improves network performance  
- Enables role-based access control  
- Contains malware/breaches in isolated segments  

### Common Segments
- User LAN  
- Server VLAN  
- Management network  
- Guest Wi-Fi  
- IoT/OT devices  

Segmentation is a fundamental part of **zero-trust architectures** and defense-in-depth strategies.
