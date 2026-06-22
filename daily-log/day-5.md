# 🛡️ Cybersecurity Journey: Day 5 - IP Addressing & Subnetting

This log covers the foundational architecture of computer networks. Mastering how networks are divided is essential for network engineering, defense, and penetration testing.

---

## 🌐 The Fundamentals of IPv4
An IP address is the digital "postal address" for a device. 
* **Structure:** 32-bit address represented as 4 octets (0-255).
* **Composition:** Network ID (the neighborhood) + Host ID (the specific house).

### Binary Translation
Computers think in bits. To understand subnet masks, you must know how to convert decimal to binary:
| Decimal | Binary (8-bit) |
| :--- | :--- |
| 0 | 00000000 |
| 1 | 00000001 |
| 128 | 10000000 |
| 255 | 11111111 |

---

## 🧩 Mastering Subnetting
Subnetting is the process of creating smaller, isolated "neighborhoods" within a large network. This limits "noise" and enhances security.

### The "256 Rule" (Simplified Calculation)
Instead of complex binary math, use this "Chunking" method to determine your network range:
1. **Identify the Subnet Mask** (e.g., `255.255.255.192`).
2. **Subtract the last octet from 256**: $256 - 192 = 64$.
3. **The Result (64)** is your "Magic Number." Your networks increase in jumps of 64:
   * **Network 1:** 0 – 63
   * **Network 2:** 64 – 127
   * **Network 3:** 128 – 191
   * **Network 4:** 192 – 255

> **Important:** Always subtract 2 addresses from the total count in any subnet. One is for the **Network Address** (the street sign), and one is for the **Broadcast Address** (the megaphone).

---

## 🔐 Why This is Vital for Cybersecurity

### 1. Precision Scanning (Nmap)
Using tools like Nmap blindly is loud and inefficient. By calculating subnets, I can target only the relevant host ranges, keeping my scans quiet and focused.

### 2. Identifying Lateral Movement
Understanding subnet boundaries helps me identify how an attacker moves. If I know a server is on a specific subnet, I can identify which other devices share that "neighborhood" and harden the communication between them.

### 3. Firewall Policy Design
Subnetting allows for **Micro-segmentation**. If a company puts all servers in one subnet and all guest devices in another, a firewall can effectively block "Guest" traffic from ever reaching the "Server" subnet. I learned how to identify these "walls" to ensure security is working as intended.

---

## 🛠️ Tools Used
* **Nmap:** For network reconnaissance.
* **Mental Math (256 Rule):** For rapid network range calculation.

## 🛠️ Hands-on: Analyzing Subnets with `ipcalc`

To verify network segments, I used the `ipcalc` tool in Kali Linux. Below is an analysis of a `/29` subnet, which is commonly used for small, high-security server clusters.

```bash
mrx@kali:~$ ipcalc 10.50.75.200/29
Address:   10.50.75.200         00001010.00110010.01001011.11001 000
Netmask:   255.255.255.248 = 29 11111111.11111111.11111111.11111 000
Wildcard:  0.0.0.7              00000000.00000000.00000000.00000 111
=>
Network:   10.50.75.200/29      00001010.00110010.01001011.11001 000
HostMin:   10.50.75.201         00001010.00110010.01001011.11001 001
HostMax:   10.50.75.206         00001010.00110010.01001011.11001 110
Broadcast: 10.50.75.207         00001010.00110010.01001011.11001 111
Hosts/Net: 6                    Class A, Private Internet
```

### 📌 Explanation of Important Values

| Item | Address | Description |
|--------|---------|-------------|
| **Network Address** | `10.50.75.200/29` | Represents the subnet (network segment) |
| **First Usable Host** | `10.50.75.201` | First IP address available for devices |
| **Last Usable Host** | `10.50.75.206` | Last IP address available for devices |
| **Broadcast Address** | `10.50.75.207` | Used to send packets to all devices in the subnet |
| **Usable Hosts** | `6` | Maximum number of devices that can be assigned IP addresses |

### 📝 What Each Line Means

- **Network:** `10.50.75.200/29`  
  This is the main network or "neighborhood" that contains all addresses in the subnet.

- **HostMin:** `10.50.75.201`  
  The first usable IP address that can be assigned to a device.

- **HostMax:** `10.50.75.206`  
  The last usable IP address available for devices.

- **Broadcast:** `10.50.75.207`  
  The "loudspeaker" address used to communicate with every device in the subnet simultaneously.

- **Hosts/Net:** `6`  
  Indicates that up to **6 devices** can have unique IP addresses within this `/29` subnet.

---
**Status:** ✅ Day 5 Complete
**Focus:** Building a strong technical foundation for future infrastructure security analysis.
