# 🛠️ Cybersecurity Tools Documentation

Welcome to the tools repository. This section documents my hands-on experience, installation steps, configuration guides, and practical commands for industry-standard cybersecurity utilities.

The focus here is moving from abstract networking theory to active system analysis, reconnaissance, and traffic inspection.

---

## 🔍 Active Tool Index

<details>
<summary><b>📦 Nmap (Network Mapper)</b></summary>

### 🛠️ Core Overview
Learned via NetworkChuck's excellent tutorial: **[Nmap Tutorial to find Network Vulnerabilities](https://www.youtube.com/watch?v=4t4kBkMsDbQ)**.

**Nmap** is the de-facto standard tool for network discovery, port scanning, service enumeration, and active reconnaissance. Pentesters and red teamers rely on it heavily during the **Information Gathering** and **Scanning & Enumeration** phases of the PTES / OSCP methodology.

### 📥 Installation
```bash
sudo apt update && sudo apt install nmap -y
```

### 🚀 Essential Pentester Commands

#### 1. Host Discovery & Recon
```bash
nmap -sn 192.168.1.0/24              # Quick host discovery
nmap -Pn -sS target                  # Skip host discovery + stealth scan
```

#### 2. Port Scanning Techniques
```bash
nmap -sS target                      # SYN Stealth (default for pentesters)
nmap -sT target                      # TCP Connect (when no raw socket privileges)
nmap -sA target                      # ACK scan (firewall rule mapping)
nmap -sU target                      # UDP scan (slower but important)
nmap -p- -T4 target                  # All ports + aggressive timing
nmap -F -T4 target                   # Fast scan (top 100 ports)
```

#### 3. Service, Version & OS Enumeration
```bash
nmap -sV target                      # Service version detection (critical)
nmap -O --osscan-guess target        # OS detection + aggressive guessing
nmap -A target                       # Aggressive scan (OS + Version + Scripts + Traceroute)
```

#### 4. Scripting Engine (NSE) - Pentester's Best Friend
```bash
nmap -sC target                      # Default safe scripts
nmap --script vuln target            # Vulnerability detection scripts
nmap --script http-enum target       # Enumerate web directories
nmap --script smb-vuln* target       # SMB vulnerabilities
nmap --script ftp* target            # FTP brute force / anon access
nmap --script default,safe,vuln target
```

#### 5. Evasion & Stealth Techniques
```bash
nmap -D RND:15 target                # 15 random decoys
nmap -D 192.168.1.100,192.168.1.101 target  # Specific decoy IPs
nmap --spoof-mac 0 target            # Random MAC address
nmap --data-length 25 target         # Append random data to packets
nmap -T2 target                      # Slower timing to evade IDS
nmap --source-port 53 target         # Spoof source port (DNS)
```

#### 6. Output & Reporting
```bash
nmap -oN scan.txt target             # Normal output
nmap -oX scan.xml target             # XML (import into Metasploit, Dradis)
nmap -oA scan_results target         # All formats (Normal + XML + Grepable)
nmap -v -oN scan.txt target          # Verbose output
```

### 💀 Pentester's Recommended Workflow
```bash
# Phase 1: Discovery
nmap -sn 192.168.1.0/24 -oN live_hosts.txt

# Phase 2: Detailed Scan
nmap -sS -sV -O -T4 -p- --open 192.168.1.100 -oN detailed_scan.txt

# Phase 3: Deep Enumeration + Vulns
nmap -sV -sC --script vuln -T4 192.168.1.100 -oN vuln_scan.txt
```

### 📝 Day 11 Learning Notes
- Understood TCP 3-way handshake and difference between **-sT** vs **-sS**.
- Learned how version detection (`-sV`) turns open ports into exploitable intelligence.
- Mastered basic evasion techniques and the power of the **Nmap Scripting Engine (NSE)**.
- Ready to integrate Nmap output with Metasploit / exploitation frameworks.

**Status**: Solid foundational and pentester-level proficiency with Nmap.

</details>
