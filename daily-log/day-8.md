# 🛡️ Cybersecurity Journey: Day 8 - TCP/IP, DNS, IPv4 & Subnetting

## 📖 Overview

Today I focused on understanding how devices communicate across networks using the TCP/IP model, DNS, IP addressing, routing, and subnetting. These concepts form the foundation of networking and cybersecurity because every attack, scan, or defense mechanism relies on network communication.

By the end of the day, I was able to analyze network configurations, perform DNS lookups, trace packet routes across the Internet, and manually calculate subnet information without relying entirely on tools.

---

# 🌐 The TCP/IP Model

The TCP/IP model is the practical networking model used by the Internet. Unlike the OSI model, it contains four layers.

| Layer       | Function                                      |
| ----------- | --------------------------------------------- |
| Application | Provides services for user applications       |
| Transport   | Handles communication between hosts (TCP/UDP) |
| Internet    | Responsible for IP addressing and routing     |
| Link        | Handles communication on the local network    |

---

## Layer 4: Application Layer

The Application Layer allows software and applications to communicate over the network.

### Common Protocols

* HTTP / HTTPS
* DNS
* FTP
* SMTP
* SSH

### DNS Name Resolution

DNS translates human-readable names into IP addresses.

Example:

```bash
nslookup google.com
```

Output:

```text
google.com -> 64.233.161.102
```

This allows users to access websites without remembering IP addresses.

---

## Layer 3: Transport Layer

The Transport Layer manages end-to-end communication.

### TCP

Features:

* Reliable
* Connection-oriented
* Error checking
* Flow control

Examples:

* HTTPS
* SSH
* FTP

### UDP

Features:

* Faster
* Connectionless
* No delivery guarantee

Examples:

* DNS
* Streaming
* Online gaming

---

# 🌎 Layer 2: Internet Layer

The Internet Layer handles:

* Logical Addressing
* Routing
* Packet Forwarding

### Common Protocols

* IPv4
* IPv6
* ICMP
* IPsec
* OSPF
* RIP

---

## ICMP and Ping

ICMP is used for diagnostics and troubleshooting.

Example:

```bash
ping -4 google.com -c 4
```

Result:

```text
4 packets transmitted
4 received
0% packet loss
```

This confirms connectivity between my machine and Google's servers.

---

## Traceroute

Traceroute shows every router a packet passes through on its journey.

Example:

```bash
traceroute google.com
```

This revealed multiple hops between my system and Google, demonstrating how packets are routed through the Internet.

---

# 🔍 DNS Analysis

### nslookup

```bash
nslookup google.com
```

Purpose:

* Resolves domain names
* Shows DNS server responses

### dig

```bash
dig google.com
```

Purpose:

* Detailed DNS analysis
* Query statistics
* TTL values
* DNS server information

---

# 📍 IPv4 Addressing

An IPv4 address consists of 32 bits divided into four octets.

Example:

```text
192.168.100.50
```

Binary representation:

```text
11000000.10101000.01100100.00110010
```

IPv4 provides logical addressing so devices can communicate across different networks.

---

# 🏠 My Network Configuration

Using:

```bash
ip a
ip route
```

I identified:

```text
IP Address : 192.168.100.50
Gateway    : 192.168.100.1
Subnet     : 192.168.100.0/24
```

---

# 🚪 Default Gateway

The default gateway is the router responsible for forwarding traffic outside the local network.

My gateway:

```text
192.168.100.1
```

Traffic flow:

```text
My PC
   ↓
Router (Gateway)
   ↓
Internet
   ↓
Destination
```

---

# 📢 Broadcast Address

A broadcast address allows communication with every host in a subnet.

Example:

```text
192.168.100.255
```

A packet sent to the broadcast address reaches all devices in the network.

---

# 🎯 CIDR Notation

CIDR (Classless Inter-Domain Routing) represents the subnet mask using a suffix.

Example:

```text
192.168.100.50/24
```

Equivalent subnet mask:

```text
255.255.255.0
```

---

# 🧮 Subnetting

Subnetting divides networks into smaller segments.

### Common CIDR Values

| CIDR | Subnet Mask     | Hosts |
| ---- | --------------- | ----- |
| /24  | 255.255.255.0   | 254   |
| /25  | 255.255.255.128 | 126   |
| /26  | 255.255.255.192 | 62    |
| /27  | 255.255.255.224 | 30    |
| /28  | 255.255.255.240 | 14    |
| /29  | 255.255.255.248 | 6     |
| /30  | 255.255.255.252 | 2     |

---

## Practical Example

Network:

```text
192.168.100.50/24
```

Calculated:

```text
Network Address   : 192.168.100.0
Broadcast Address : 192.168.100.255
First Host        : 192.168.100.1
Last Host         : 192.168.100.254
Usable Hosts      : 254
```

---

## Advanced Subnetting Practice

### Example

```text
192.168.10.200/27
```

Results:

```text
Network Address   : 192.168.10.192
Broadcast Address : 192.168.10.223
First Host        : 192.168.10.193
Last Host         : 192.168.10.222
Usable Hosts      : 30
```

---

# 🛠️ Tools Used

### Network Configuration

```bash
ip a
ip route
```

### DNS

```bash
nslookup google.com
dig google.com
```

### Connectivity Testing

```bash
ping -4 google.com -c 4
```

### Route Discovery

```bash
traceroute google.com
```

### Subnet Calculations

```bash
ipcalc 192.168.100.50/24
```

---

# 🎓 Key Lessons Learned

* TCP/IP is the foundation of Internet communication.
* DNS translates domain names into IP addresses.
* ICMP is used for diagnostics and network troubleshooting.
* Routers forward packets between networks.
* IPv4 addresses contain network and host portions.
* CIDR notation defines subnet size.
* Broadcast addresses communicate with all hosts in a subnet.
* Subnetting is essential for network design and penetration testing.
* Understanding subnet boundaries makes network enumeration much easier.

---

# 🚀 Day 8 Summary

Today I built a strong foundation in networking by learning how devices communicate across local and global networks. I practiced DNS resolution, packet routing, IP addressing, and subnetting while using real networking tools on Kali Linux.

This knowledge is critical for future topics such as:

* ARP
* MAC Addresses
* Ethernet
* Network Scanning
* Nmap
* Active Directory
* Internal Penetration Testing

The biggest achievement of today was learning how to calculate subnet ranges, broadcast addresses, and usable host ranges manually without relying completely on automated tools.
