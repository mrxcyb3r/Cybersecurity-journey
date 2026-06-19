# 🛡️ Cybersecurity Learning Journey

Welcome to my cybersecurity learning repository! I am documenting my daily progress, experiments, and technical findings as I build a strong foundation in ethical hacking and network security.

## 📅 Day 4: Network Reconnaissance & Traffic Analysis
Today, I moved from theory into **active network reconnaissance**. I learned how to map a local environment and observe how devices communicate at the network layer.

### 🎯 Objectives
* Understand the OSI model in a practical context.
* Perform host discovery and service scanning on a local network.
* Analyze live network traffic using packet capture tools.

### 🛠️ Tools & Methodology
* **Nmap:** Used for host discovery (`-sn`) and TCP SYN scanning (`-sS`) to identify open ports and services.
* **Wireshark:** Captured live wireless traffic on `wlan0` to inspect packets in real-time.
* **Command Line:** Utilized `ifconfig` and `ip addr` to understand network interfaces.

### 🔍 Key Findings & Experiments
1. **Network Mapping:** Successfully identified my local gateway (`192.168.100.1`) and confirmed it as a Huawei device via MAC address lookup.
2. **Port Analysis:** Identified open services (HTTP/DNS) and filtered ports (SSH/FTP/Telnet) on the router. 
3. **Traffic Sniffing:** Captured real-time traffic to observe background communication between my machine and external services.

---

## 📚 Reference: Essential Network Protocols
To build a solid foundation, I studied the core protocols that govern internet communication:

### Core Internet Infrastructure
* **TCP/IP:** The foundation. *TCP* ensures reliability via a three-way handshake; *IP* handles device addressing.
* **UDP:** A connectionless protocol prioritized for speed (gaming, streaming).
* **DNS:** The "phone book" translating domain names to IP addresses.
* **DHCP:** Automates the assignment of IP addresses.

### Web & File Management
* **HTTP/HTTPS:** The standard for web browsing. *HTTPS* adds *TLS/SSL* encryption for security.
* **FTP/SFTP:** Methods for file transfers; *SFTP* adds necessary encryption layers.
* **SSH:** A secure method for remote server management, replacing insecure *Telnet*.

### Communication & Advanced Protocols
* **SMTP:** The core protocol for sending email.
* **TLS/SSL:** The "invisible bodyguard" for internet encryption.
* **WebSocket:** Persistent, real-time, two-way communication.
* **QUIC:** Modern protocol combining TCP’s reliability with UDP’s speed.
* **BGP:** The internet’s "ultimate navigator" for global routing paths.

---

*“Cybersecurity is not about learning everything. It's about learning the right things in the right order.”*

