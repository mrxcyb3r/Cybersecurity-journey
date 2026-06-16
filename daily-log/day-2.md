# 🟢 Day 2: Network Protocols, The Web, and Core Infrastructure

**Date:** June 16, 2026  
**Method:** Independent Self-Study  
**Core Focus:** How data finds, accesses, and securely moves across web services.

---

## 🚪 Part 1: Ports and Protocols (The Doors of a Server)

To establish communication, networks rely on rules to format data and specific endpoints to receive it.
- **Network Protocol:** A standardized set of rules that determines how data is formatted, transmitted, and received. It is the common language computers agree to speak.
- **Port:** A virtual endpoint on an operating system (numbered from `0` to `65535`) dedicated to a specific service or protocol.

### 📦 Real-Life Example
Imagine a massive **Corporate Office Building** (The Server / Destination IP Address). Inside this building, there are different specialized departments:
- **Room 80** is the Web Design department.
- **Room 22** is the Secure Vault where managers remotely log into the building's infrastructure.
- **Room 21** is the Loading Dock used exclusively for moving heavy boxes of corporate files.

If you mail a package to the building, you must specify the exact room number on the envelope. If you omit it, the front desk won't know where to send the delivery, and the connection fails.

### 💀 Offensive Security Context: Port Scanning
As an offensive operator, finding open ports is the first step of an active attack. Red Teamers use network scanners (like `nmap`) to probe a target IP address and see which ports are "open" (actively listening for incoming connections). Discovering an open Port 21 (FTP) tells you exactly what software service is running, allowing you to immediately search for known exploits or configuration flaws specific to that file-sharing service.

---

## 📇 Part 2: DNS (The Phonebook of the Internet)

Computers communicate using numeric identifiers like IP addresses (`142.250.190.46`), but humans remember text-based names like `google.com`. **DNS (Domain Name System)** bridges this gap by acting as a distributed lookup infrastructure.

### 🔄 How it Works: The DNS Request Flow
When you type a domain name into a browser, your machine executes a rapid, multi-step lookup sequence:
1. **The Browser:** Checks its internal memory. If unknown, it queries the local operating system.
2. **The OS Cache:** Checks its local records. If unknown, it forwards the request outward to a **DNS Resolver** (typically hosted by your ISP or a public provider like Cloudflare's `1.1.1.1`).
3. **The Resolver:** Queries a global hierarchy of root, top-level domain (`.com`), and authoritative servers until it locates the matching IP address.
4. **The Connection:** The resolver returns the IP address to your browser, which finally initiates a direct connection to the target server.

### 📦 Real-Life Example
Think of DNS exactly like the **Contacts App on your smartphone**. You do not memorize your friends' 10-digit phone numbers; you simply search and tap their names. Your phone queries its internal database, maps the name to the designated number, and dials it behind the scenes.

### 💀 Offensive Security Context: DNS Spoofing
If an attacker manipulates the phonebook, they control the traffic. In a **DNS Spoofing** (or Cache Poisoning) attack, a hacker injects false routing records into a local router or DNS server. They change the mapping so that a legitimate domain like `bankofamerica.com` points directly to the *attacker's* malicious IP address. When a victim types the correct web address, they are silently sent to a perfect visual clone of the bank website, where the attacker captures their login credentials in real-time.

---

## 🕸️ Part 3: HTTP vs. HTTPS (The Language of the Web)

Understanding web data transit is crucial for web application hacking and Bug Bounty programs. **HTTP (Hypertext Transfer Protocol)** is the language used to request and serve web pages.

### 🔓 1. HTTP (Unencrypted / Cleartext)
- **Concept:** Data is transmitted in raw, unencrypted text across the network.
- **📦 Real-Life Example:** Imagine writing a private message on the back of a **postcard** and dropping it in a public mailbox. Every postal worker, truck driver, and sorting facility clerk who handles that card can read your text. If you type a password into a plain HTTP website, anyone intercepting packets on that same network (e.g., public Wi-Fi) can read it instantly using a basic packet sniffer.

### 🔒 2. HTTPS (Encrypted / Secure)
- **Concept:** Uses **TLS (Transport Layer Security)** to cryptographically scramble data before it ever leaves your network interface card.
- **📦 Real-Life Example:** Imagine placing that same private message inside a **heavy-duty steel lockbox** before shipping it. Observers can see the box's destination label, but only the intended recipient possesses the private cryptographic key required to unlock the box and read the contents.

---

## ⚡ Day 2 Reference: Core Ports to Memorize

These well-known ports appear constantly during asset discovery and network analysis:

| Port | Protocol | Primary Purpose | Primary Security Risk |
| :--- | :--- | :--- | :--- |
| **21** | **FTP** (File Transfer Protocol) | Moving files between systems. | Transmits credentials and data in cleartext. |
| **22** | **SSH** (Secure Shell) | Secure remote command-line access. | Safe if configured right; highly targeted for brute-force password attacks. |
| **80** | **HTTP** | Serving unencrypted web content. | Data is completely open to sniffing and interception. |
| **443** | **HTTPS** | Serving encrypted web traffic. | Modern standard; protects data integrity in transit. |