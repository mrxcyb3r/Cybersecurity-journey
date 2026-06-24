# 🛡️ Cybersecurity Learning Log: Day 7

## Network Architecture, Segmentation, Topologies & Proxy Systems

> Understanding how networks are designed is essential for both defenders and penetration testers. Today's focus was on network segmentation, enterprise architectures, network topologies, proxy systems, and the OSI model.

---

# 📚 Overview

Today's study session explored how enterprise networks are structured and why architecture directly affects both security and attack surfaces.

By understanding network layouts, subnet boundaries, communication paths, and proxy technologies, security professionals can better identify risks, detect threats, and conduct accurate assessments.

---

# 🔐 1. Network Segmentation & The Flat Network Problem

## What is a Flat Network?

A flat network places all hosts inside a single broadcast domain, allowing unrestricted communication between systems.

### Risks

* Easy lateral movement after compromise
* Lack of internal security boundaries
* Increased attack surface
* Difficult traffic monitoring

### Security Controls

#### Access Control Lists (ACLs)

Used to restrict communication between network segments.

**Example:**

* Printer VLAN cannot access application servers
* Guest network cannot reach internal resources

#### Network Mapping

Helps identify:

* Unexpected communication paths
* Unauthorized internet access
* Misconfigured systems

#### Intrusion Detection Systems (IDS)

Common IDS platforms:

* Snort
* Suricata

These systems detect activities such as:

* Port scanning
* Lateral movement
* Suspicious traffic patterns

---

## The Subnet Mask Pitfall

A common mistake during assessments is assuming every network uses a `/24` subnet.

### Example

**/24 Network**

```text
255.255.255.0
192.168.1.0 - 192.168.1.255
```

**/25 Network**

```text
255.255.255.128

Subnet A:
192.168.1.0 - 192.168.1.127

Subnet B:
192.168.1.128 - 192.168.1.255
```

Misconfigured scanning may incorrectly label hosts as offline when they actually exist in another subnet.

---

# 🏢 2. Standard 5-Tier Enterprise Network Design

Modern enterprises separate assets into isolated security zones.

## 1️⃣ DMZ (Demilitarized Zone)

Purpose:

* Hosts public-facing services
* Protects internal infrastructure

Examples:

* Web servers
* Public APIs
* Mail gateways

---

## 2️⃣ Workstation Network

Contains employee devices.

Security Goals:

* Prevent workstation-to-workstation attacks
* Reduce ransomware spread
* Enforce endpoint firewall policies

---

## 3️⃣ Administration Network

Dedicated management segment for:

* Routers
* Switches
* Firewalls

Benefits:

* Prevents unauthorized access
* Protects routing infrastructure
* Secures administrative traffic

---

## 4️⃣ VoIP Network

Separates IP phone communications.

Advantages:

* Better Quality of Service (QoS)
* Reduced eavesdropping risks
* Simplified traffic management

---

## 5️⃣ Printer Network

Printers are often overlooked security risks.

Potential Risks:

* Credential theft
* NTLM relay attacks
* Legacy vulnerabilities

Best Practices:

* No internet access
* Restricted communication
* Isolated VLAN

---

# 🌐 3. Network Topologies

Network topology defines how devices are physically and logically connected.

| Topology       | Common Use Case             | Security Consideration                |
| -------------- | --------------------------- | ------------------------------------- |
| Point-to-Point | Data center links           | Physical interception risk            |
| Bus            | Industrial systems, CAN Bus | Easy packet sniffing                  |
| Star           | Modern LANs                 | Central switch is critical            |
| Ring           | Metro fiber networks        | Visibility through intermediate nodes |
| Mesh           | Internet backbone           | Routing manipulation attacks          |
| Tree           | Enterprise campuses         | Facilitates lateral movement mapping  |
| Daisy Chain    | Temporary deployments       | Single point of failure               |
| Hybrid         | Real-world enterprises      | Attackers target weakest segment      |

---

## Point-to-Point

### Use Cases

* Dedicated fiber connections
* Site-to-site links

### Attacker Perspective

* Cable tapping
* Traffic interception

---

## Bus Topology

### Use Cases

* Industrial control systems
* Vehicle communication networks

### Attacker Perspective

* Passive sniffing
* Promiscuous mode monitoring

---

## Star Topology

### Use Cases

* Corporate LANs
* Home networks

### Attacker Perspective

* ARP spoofing attacks
* Central switch targeting

---

## Ring Topology

### Use Cases

* Metropolitan Area Networks (MAN)

### Attacker Perspective

* Interception through compromised nodes
* Token manipulation

---

## Mesh Topology

### Use Cases

* Internet backbone
* Military communications

### Attacker Perspective

* Routing protocol abuse
* Traffic redirection attacks

---

## Tree Topology

### Use Cases

* Large enterprise environments
* Campus networks

### Attacker Perspective

* Easier lateral movement planning
* High-level switch compromise impact

---

## Daisy Chain

### Use Cases

* Temporary setups
* Peripheral device chains

### Attacker Perspective

* Disrupting one node affects all downstream devices

---

## Hybrid Topology

### Use Cases

Most real-world organizations use a combination of:

* Star
* Tree
* Mesh

### Attacker Perspective

Focuses on exploiting the weakest connected segment.

---

# 🔄 4. Layer 7 Proxy Systems

A proxy acts as an intermediary between clients and servers.

Unlike simple gateways, proxies can inspect application-layer traffic.

**OSI Layer:** Layer 7 (Application Layer)

---

## Forward Proxy

Controls outbound client traffic.

### Common Uses

* Web filtering
* Content restrictions
* Traffic monitoring

### Security Impact

Malware often fails if it cannot discover proxy settings.

---

## Reverse Proxy

Handles inbound requests before they reach backend servers.

### Examples

* Cloudflare
* ModSecurity
* Nginx Reverse Proxy

### Benefits

* DDoS protection
* Traffic filtering
* Web Application Firewall (WAF) integration

### Attacker Usage

Compromised systems can be used as reverse proxies through:

```bash
SSH Tunnels
Encrypted Pivoting
Traffic Redirection
```

---

## Proxy Types

### Transparent Proxy

Characteristics:

* No client configuration required
* Intercepts traffic automatically

Examples:

* ISP filtering
* Enterprise content filtering

---

### Non-Transparent Proxy

Characteristics:

* Manual configuration required
* Browser/system settings must be updated

If not configured correctly, traffic cannot pass through the proxy.

---

# 🧩 5. Understanding the OSI Model

The OSI model provides a structured framework for understanding network communication.

Rather than memorizing layers, think of it as a data processing pipeline.

## Encapsulation

Data travels:

```text
Layer 7 → Layer 1
```

Each layer adds its own information before transmission.

---

## Decapsulation

Data travels:

```text
Layer 1 → Layer 7
```

Each layer removes and processes its corresponding information.

---

## OSI Model Breakdown

```text
[7] Application
     Human-facing protocols
     Examples: HTTP, FTP, SSH

[6] Presentation
     Translation, Encryption, Compression
     Examples: TLS, SSL, JSON

[5] Session
     Connection management
     Examples: Sessions, Sockets

[4] Transport
     Reliability and segmentation
     Examples: TCP, UDP

[3] Network
     Routing and logical addressing
     Examples: IP, Routers

[2] Data Link
     Frame handling and MAC addressing
     Examples: Ethernet Frames, Switches

[1] Physical
     Raw bit transmission
     Examples: Copper, Fiber, Wireless RF
```

---

# 🎯 Key Takeaways

✅ Network segmentation limits attacker movement

✅ Enterprise networks should be divided into security zones

✅ Different topologies create different attack opportunities

✅ Layer 7 proxies inspect application traffic and improve security

✅ Understanding the OSI model is crucial for troubleshooting, defense, and penetration testing

---

## 📅 Progress

**Day 7 Complete**

Topics Covered:

* Network Segmentation
* ACLs
* IDS
* Enterprise Network Architecture
* Network Topologies
* Forward & Reverse Proxies
* Transparent vs Non-Transparent Proxies
* OSI Model
* Encapsulation & Decapsulation
