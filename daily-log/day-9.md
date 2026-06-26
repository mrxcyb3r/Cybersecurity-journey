<div align="center">

# 🛡️ Cybersecurity Journey — Day 9

### **MAC Addresses • IPv6 • Networking Key Terminology**

**Date:** June 26, 2026

*"Understanding how devices identify each other and communicate is the foundation of every network attack and defense."*

</div>

---

# 📌 Overview

Today I focused on understanding how devices identify themselves on a local network, how IPv6 expands Internet addressing beyond IPv4, and reviewed the most important networking protocols that penetration testers encounter during security assessments.

Instead of memorizing every protocol, I concentrated on understanding **what each technology does**, **why it exists**, and **where it is commonly used** in cybersecurity.

---

# 🎯 Learning Goals

- Understand MAC addresses
- Learn how ARP resolves IP addresses to MAC addresses
- Understand IPv6 basics
- Learn common networking terminology
- Identify protocols that are important for penetration testing
- Practice networking commands in Kali Linux

---

# 🖥️ Topics Covered

## 📍 1. MAC Addresses

I learned that every network interface has a unique physical address called a **MAC (Media Access Control) address**.

Example:

```text
F0:68:E3:15:BA:96
```

Key concepts:

- 48-bit (6-byte) hardware address
- Written in hexadecimal
- Works at **OSI Layer 2 (Data Link Layer)**
- Used only inside the local network
- Every Ethernet/Wi-Fi adapter has one

---

## 📍 2. MAC Address Structure

A MAC address consists of two parts.

### Organization Unique Identifier (OUI)

The first 24 bits identify the manufacturer.

Example:

```text
F0:68:E3
```

---

### NIC (Device Identifier)

The last 24 bits uniquely identify the network card.

Example:

```text
15:BA:96
```

Together they create a globally unique hardware address.

---

## 📍 3. IP Address vs MAC Address

| IP Address | MAC Address |
|------------|-------------|
| Logical Address | Physical Address |
| Layer 3 | Layer 2 |
| Can change | Usually permanent |
| Used across the Internet | Used only inside the LAN |

Simple analogy:

- **IP Address → House Address**
- **MAC Address → Person inside the house**

---

## 📍 4. Address Resolution Protocol (ARP)

ARP converts an IP address into a MAC address.

Communication process:

```text
Computer
      │
      ▼
Who has 192.168.100.1?
      │
      ▼
Router replies
      │
      ▼
My MAC is
AA:BB:CC:DD:EE:FF
```

After ARP resolution, communication can begin.

---

## 📍 5. ARP Request & Reply

### ARP Request

Broadcast message sent to everyone.

Example:

```text
Who has 192.168.100.1?
Tell 192.168.100.50
```

---

### ARP Reply

Only the correct device responds.

Example:

```text
192.168.100.1 is at
AA:BB:CC:DD:EE:FF
```

---

## 📍 6. Broadcast, Unicast & Multicast

### Unicast

One sender → One receiver

---

### Broadcast

One sender → Everyone

Broadcast MAC:

```text
FF:FF:FF:FF:FF:FF
```

---

### Multicast

One sender → Selected group of receivers

---

## 📍 7. ARP Spoofing

I learned how attackers can poison the ARP cache by pretending to be another device.

Possible attacks include:

- Man-in-the-Middle (MITM)
- Packet interception
- Credential theft
- Traffic manipulation

Important takeaway:

> MAC addresses should never be trusted as the only security mechanism.

---

# 🌍 IPv6

Today I also learned the basics of IPv6.

Example:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

Key concepts:

- 128-bit addresses
- Much larger address space than IPv4
- Uses hexadecimal notation
- Supports modern Internet growth
- Eliminates IPv4 exhaustion

Compared to IPv4:

| IPv4 | IPv6 |
|------|------|
| 32-bit | 128-bit |
| Decimal | Hexadecimal |
| ~4.3 Billion addresses | 340 undecillion addresses |

---

# 🌐 Networking Key Terminology

I reviewed the networking protocols that are most useful for penetration testing.

## Core protocols to master

| Protocol | Purpose |
|----------|---------|
| HTTP | Web communication |
| HTTPS | Secure web communication |
| DNS | Domain name resolution |
| SSH | Secure remote login |
| FTP | File transfer |
| SMB | Windows file sharing |
| NFS | Linux file sharing |
| SMTP | Email transfer |
| SNMP | Network device management |
| DHCP | Automatic IP assignment |
| ICMP | Ping and network diagnostics |
| LDAP | Active Directory directory service |
| Kerberos | Authentication |
| RDP | Remote Desktop |

Instead of memorizing every protocol, I focused on understanding **how attackers interact with these services during penetration tests.**

---

# 🛠️ Kali Linux Commands Practiced

## View network interfaces

```bash
ip a
```

---

## View routing table

```bash
ip route
```

---

## View ARP cache

```bash
ip neigh
```

or

```bash
arp -a
```

---

## Test connectivity

```bash
ping google.com
```

IPv4 only:

```bash
ping -4 google.com
```

---

## Trace packet path

```bash
traceroute google.com
```

---

## DNS lookup

```bash
nslookup google.com
```

---

## Advanced DNS lookup

```bash
dig google.com
```

---

# 💡 Key Takeaways

- Every network adapter has a unique MAC address.
- IP addresses identify devices across networks, while MAC addresses identify devices on the local network.
- ARP translates IP addresses into MAC addresses.
- Broadcast messages are sent to every device on the LAN.
- ARP spoofing is a common attack used in Man-in-the-Middle scenarios.
- IPv6 provides a much larger address space than IPv4.
- A penetration tester does not memorize every protocol—understanding the most common ones and knowing how to enumerate them is far more valuable.

---

# 📚 Skills Improved

- Network fundamentals
- Layer 2 communication
- ARP resolution
- MAC addressing
- IPv6 basics
- Protocol recognition
- Kali Linux networking tools

---

# 🚀 Next Steps

Tomorrow I will continue with:

- Common Network Protocols (TCP vs UDP)
- Service Enumeration
- Port-based communication
- Hands-on protocol analysis
- Practical penetration testing techniques

---

<div align="center">

## ✅ Day 9 Complete

**"Every packet has a destination. Every pentester should understand how it gets there."**

</div>
