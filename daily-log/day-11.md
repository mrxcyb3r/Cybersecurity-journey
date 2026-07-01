# 🟢 Day 11: Nmap - Network Discovery & Enumeration

**Date:** July 01, 2026  
**Focus:** Mastering Nmap for Host Discovery, Port Scanning, Service Enumeration & Vulnerability Hunting.

---

## 🛠️ Nmap Command Reference (Cybersecurity Learning)

### 1. Host Discovery (Ping Sweep)
* **`nmap -sn 192.168.1.0/24`** : Discover live hosts on a network (no port scan).
* **`nmap -sP 10.0.0.0/24`** : Traditional ping sweep.
* **`nmap -Pn target`** : Skip host discovery (treat all hosts as online).

### 2. Basic Port Scanning
* **`nmap target`** : Default scan (top 1000 ports).
* **`nmap -sT target`** : TCP Connect scan (full 3-way handshake — loud but reliable).
* **`nmap -sS target`** : SYN/Stealth/Half-Open scan (most popular — stealthier).
* **`nmap -F target`** : Fast scan (top 100 ports).
* **`nmap -p- target`** : Scan all 65,535 ports.
* **`nmap -p 80,443,22 target`** : Scan specific ports.

### 3. Service & Version Detection
* **`nmap -sV target`** : Detect service versions on open ports (highly recommended).
* **`nmap -sV -sC target`** : Service version + default Nmap scripts.

### 4. OS Detection & Aggressive Scanning
* **`nmap -O target`** : Operating System detection/fingerprinting.
* **`nmap -A target`** : **Aggressive mode** (OS detection + version + scripts + traceroute).

### 5. Advanced & Evasion Techniques
* **`nmap -D RND:10 target`** : Use 10 random decoys (hides your real IP).
* **`nmap -T4 target`** : Timing template (0=slowest, 5=fastest; T4 is good balance).
* **`nmap --script vuln target`** : Run vulnerability detection scripts.
* **`nmap -sC --script=default target`** : Run default safe scripts.

### 6. Output & Documentation
* **`nmap -oN scan.txt target`** : Save output to normal text file.
* **`nmap -oX scan.xml target`** : Save as XML (great for tools like Metasploit).
* **`nmap -v target`** : Verbose output (see progress in real-time).

---

## 💀 Core Scanning Workflow (Enumeration Methodology)

Professional recon flow:
1. **`nmap -sn 192.168.1.0/24`** → Find live hosts.
2. **`nmap -sS -sV -O -T4 target`** → Stealth scan + services + OS.
3. **`nmap -sV -sC --script vuln target`** → Deep service enumeration + vuln checking.
4. **`nmap -A target`** → Full aggressive recon when allowed.

---

## 📝 Learning Summary

Today I learned Nmap — the de facto standard for network mapping and reconnaissance. I now understand:

- The difference between **TCP Connect (-sT)** and **SYN Stealth (-sS)** scans.
- How the TCP 3-way handshake works and why stealth scans are preferred.
- Service/version detection (`-sV`), OS fingerprinting (`-O`), and the power of the Nmap Scripting Engine (NSE).
- Basic evasion with decoys and timing controls.

I can now quickly map networks, identify open services, detect operating systems, and hunt for low-hanging vulnerabilities.

*Based on NetworkChuck's "Nmap Tutorial to find Network Vulnerabilities" → [Watch Here](https://www.youtube.com/watch?v=4t4kBkMsDbQ)*
