# 🌐 Day 10 — Networking Protocols, Wireless Networks & VPN Fundamentals

> A solid understanding of networking is essential for penetration testing. Every attack begins with reconnaissance, where identifying services, protocols, and network configurations helps reveal potential attack vectors.

---

# 📖 Overview

This document covers the networking concepts every aspiring penetration tester should understand:

* Common networking protocols
* Wireless networking fundamentals
* Wireless security
* Virtual Private Networks (VPNs)
* IPsec fundamentals
* VPN protocols
* Common attack vectors

The goal is **not to memorize every protocol**, but to understand how they work, where they are used, and why they matter during security assessments.

---

# 🌍 Common Networking Protocols

A **network protocol** is a set of rules that defines how devices communicate across a network.

During reconnaissance, protocols help identify:

* Running services
* Available attack surfaces
* Possible vulnerabilities

## Most Important Protocols

| Protocol | Full Name                           | Port   | Purpose               | Pentesting Importance |
| -------- | ----------------------------------- | ------ | --------------------- | --------------------- |
| HTTP     | HyperText Transfer Protocol         | 80     | Web traffic           | ⭐⭐⭐⭐⭐                 |
| HTTPS    | HyperText Transfer Protocol Secure  | 443    | Encrypted web traffic | ⭐⭐⭐⭐⭐                 |
| SSH      | Secure Shell                        | 22     | Secure remote login   | ⭐⭐⭐⭐⭐                 |
| FTP      | File Transfer Protocol              | 21     | File transfer         | ⭐⭐⭐⭐                  |
| SMB      | Server Message Block                | 445    | Windows file sharing  | ⭐⭐⭐⭐⭐                 |
| DNS      | Domain Name System                  | 53     | Resolves domain names | ⭐⭐⭐⭐⭐                 |
| SMTP     | Simple Mail Transfer Protocol       | 25     | Email transfer        | ⭐⭐⭐                   |
| SNMP     | Simple Network Management Protocol  | 161    | Network management    | ⭐⭐⭐⭐                  |
| NFS      | Network File System                 | 2049   | Linux file sharing    | ⭐⭐⭐⭐                  |
| DHCP     | Dynamic Host Configuration Protocol | 67/68  | Assigns IP addresses  | ⭐⭐⭐                   |
| NTP      | Network Time Protocol               | 123    | Synchronizes time     | ⭐⭐                    |
| VPN      | Virtual Private Network             | Varies | Secure remote access  | ⭐⭐⭐⭐                  |

---

# 🔍 Why Protocols Matter

When performing reconnaissance, the first step is identifying services.

Examples:

* HTTP → Web Applications
* HTTPS → Secure Websites
* SSH → Remote Administration
* SMB → Windows Networks
* DNS → Information Gathering
* FTP → File Access
* SNMP → Device Enumeration
* NFS → Linux Shares

Knowing what each protocol does allows a penetration tester to choose the correct enumeration tools and attack techniques.

---

# 📡 Wireless Networks

Wireless networks use **radio frequencies (RF)** instead of physical cables to connect devices.

A wireless network consists of:

```
Laptop
     │
 Smartphone
     │
 Tablet
     │
   Wireless Access Point (WAP)
     │
     ▼
   Router
     │
     ▼
 Internet
```

Devices communicate over:

* 2.4 GHz
* 5 GHz

using the **IEEE 802.11** standard.

---

# 📶 Wireless Access Point (WAP)

**WAP** stands for **Wireless Access Point**.

A WAP connects wireless devices to a wired network and the Internet.

Most home routers combine:

* Router
* Switch
* Firewall
* Wireless Access Point

into one device.

---

# 📛 SSID

**SSID (Service Set Identifier)** is the Wi-Fi network name.

Example:

```
Home WiFi
Office
Coffee Shop
```

Although an SSID can be hidden, it can still be discovered by capturing wireless traffic.

---

# 🆔 MAC Address

Every network interface has a unique **Media Access Control (MAC) Address**.

Example:

```
00:1A:2B:3C:4D:5E
```

MAC addresses operate at **Layer 2** of the OSI model and are used for communication within the local network.

Attackers often spoof MAC addresses to bypass network restrictions.

---

# 🔒 Wireless Security

Wireless networks protect traffic using encryption.

## WEP (Wired Equivalent Privacy)

* RC4 encryption
* Easily broken
* Deprecated
* Never use

---

## WPA (Wi-Fi Protected Access)

Improved WEP but now outdated.

---

## WPA2 (Wi-Fi Protected Access II)

Current standard for most networks.

Uses:

* AES encryption
* Strong authentication

---

## WPA3 (Wi-Fi Protected Access III)

Newest wireless security standard.

Improvements include:

* Better encryption
* Protection against offline password attacks
* Stronger authentication

---

# 🔑 Wireless Authentication

## WPA-Personal

Uses a **Pre-Shared Key (PSK)**.

Common in homes.

---

## WPA-Enterprise

Uses centralized authentication.

Common authentication servers:

* RADIUS
* TACACS+

Widely used in businesses.

---

# ⚔️ Common Wireless Attacks

## WEP Cracking

Recover encryption keys due to WEP weaknesses.

---

## WPA Handshake Capture

Capture authentication handshake.

Attempt offline password cracking.

---

## Deauthentication Attack

Force clients to disconnect.

Capture the handshake when they reconnect.

---

## Evil Twin Attack

Create a fake wireless access point using the same SSID.

Victims unknowingly connect to the attacker.

---

## MAC Spoofing

Change your MAC address to impersonate another device.

Often used to bypass MAC filtering.

---

# 🛡️ Wireless Hardening

Secure wireless networks by:

* WPA2 or WPA3
* Strong passwords
* Enterprise authentication
* Disable WEP
* Disable WPS
* Monitor rogue access points

---

# 🔐 Virtual Private Network (VPN)

A **Virtual Private Network (VPN)** creates an encrypted tunnel between a remote device and a private network.

```
Internet
     │
Encrypted Tunnel
     │
VPN Server
     │
Internal Company Network
```

After authentication, users receive an internal IP address and can securely access company resources.

---

# 🎯 Why VPNs Matter

Organizations expose VPN gateways instead of exposing internal servers.

Penetration testers often:

* Discover VPN portals
* Test authentication
* Identify outdated VPN software
* Assess encryption strength

---

# 🔑 VPN Components

| Component      | Purpose                   |
| -------------- | ------------------------- |
| VPN Client     | Connects to VPN           |
| VPN Server     | Accepts VPN connections   |
| Authentication | Verifies users            |
| Encryption     | Protects traffic          |
| Tunnel         | Secure communication path |

---

# 🌐 Common VPN Protocols

## IPsec (Internet Protocol Security)

Enterprise VPN standard.

Provides:

* Encryption
* Authentication
* Integrity

---

### Transport Mode

Encrypts only the payload.

```
IP Header | Encrypted Data
```

---

### Tunnel Mode

Encrypts the entire packet.

```
New IP Header
Encrypted Original Packet
```

Most VPN deployments use Tunnel Mode.

---

## Authentication Header (AH)

Provides:

* Authentication
* Integrity

Does **NOT** encrypt data.

---

## Encapsulating Security Payload (ESP)

Provides:

* Encryption
* Authentication
* Integrity

Most commonly used IPsec protocol.

---

## Internet Key Exchange (IKE)

Negotiates encryption keys before the VPN tunnel is established.

Common ports:

```
UDP/500
UDP/4500 (NAT-T)
```

---

## PPTP (Point-to-Point Tunneling Protocol)

Legacy VPN protocol.

Default Port:

```
TCP/1723
```

Weaknesses:

* MSCHAPv2
* Weak encryption
* Deprecated

Modern organizations use:

* IPsec
* OpenVPN
* WireGuard
* IKEv2

---

# 🔍 VPN Enumeration

Common VPN ports:

| Port     | Service           |
| -------- | ----------------- |
| UDP/500  | IKE               |
| UDP/4500 | IPsec NAT-T       |
| TCP/1723 | PPTP              |
| TCP/443  | SSL VPN / OpenVPN |

Useful command:

```bash
nmap -sV target.com
```

---

# ⚠️ Common VPN Weaknesses

Penetration testers often discover:

* Weak passwords
* Missing MFA
* Outdated VPN software
* Old SSL/TLS versions
* Misconfigured VPN gateways

---

# 💼 Why These Topics Matter for Penetration Testing

Understanding networking allows you to:

* Enumerate hosts
* Identify services
* Discover exposed ports
* Recognize insecure protocols
* Attack outdated wireless networks
* Assess VPN security
* Plan exploitation paths

Without networking knowledge, penetration testing becomes guesswork.

---

# 📝 Key Takeaways

* Protocols define how devices communicate.
* HTTP, HTTPS, SSH, SMB, DNS, FTP, SNMP, and NFS are the most important services to recognize.
* Wireless networks rely on WAPs, SSIDs, MAC addresses, and IEEE 802.11.
* WPA2 and WPA3 provide strong wireless security.
* WEP is obsolete and insecure.
* Common wireless attacks include WEP cracking, handshake capture, deauthentication, Evil Twin, and MAC spoofing.
* VPNs provide secure remote access through encrypted tunnels.
* IPsec is the industry-standard enterprise VPN protocol.
* ESP encrypts VPN traffic, while AH provides authentication and integrity.
* PPTP is deprecated and should not be used.
* Strong networking fundamentals are essential before moving into enumeration, exploitation, Active Directory, and advanced penetration testing.
