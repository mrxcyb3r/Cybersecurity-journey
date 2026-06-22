# 🛡️ Cybersecurity Journey: Day 6 - Ports, Protocols & Service Discovery

Today, I transitioned from understanding network addressing to actively interacting with network services. I learned how to identify entry points on devices, understand how TCP connections are established, and discover running services using **Nmap**.

---

## 🚪 Understanding Network Ports

Every device contains **65,535 ports**, which act as communication endpoints.

### Port States

* 🟢 **Open** – A service is listening and accepting connections.
* 🔴 **Closed** – No service is running, but the host is reachable.
* 🟡 **Filtered** – A firewall is blocking probes and hiding the port state.

---

## 📋 Common Service Ports

|   Port   | Protocol | Usage                       |
| :------: | :------: | --------------------------- |
|  **21**  |    FTP   | File Transfer (Unencrypted) |
|  **22**  |    SSH   | Secure Remote Management    |
|  **23**  |  Telnet  | Remote Access (Insecure)    |
|  **53**  |    DNS   | Domain Name Resolution      |
|  **80**  |   HTTP   | Web Traffic                 |
|  **443** |   HTTPS  | Secure Web Traffic          |
| **3389** |    RDP   | Windows Remote Desktop      |

---

## 🤝 TCP Three-Way Handshake

TCP establishes reliable communication through three steps:

1. **SYN**

   * Client initiates the connection.
   * *"Hello, are you there?"*

2. **SYN-ACK**

   * Server responds and acknowledges.
   * *"Yes, I'm here. Ready?"*

3. **ACK**

   * Client confirms.
   * *"Let's communicate."*

```text
Client                     Server
  | ---- SYN -----------> |
  | <--- SYN-ACK -------- |
  | ---- ACK -----------> |
Connection Established ✅
```

---

# 🛠️ Hands-on: Service Discovery with Nmap

I used **Nmap** with service version detection (`-sV`) to identify services running on my local gateway.

## Command

```bash
sudo nmap -sV 192.168.100.1
```

### Option Breakdown

| Option          | Meaning                                  |
| --------------- | ---------------------------------------- |
| `sudo`          | Run with administrator privileges        |
| `nmap`          | Network Mapper tool                      |
| `-sV`           | Detect service versions                  |
| `192.168.100.1` | Target IP address (local gateway/router) |

---

## Output

```bash
Starting Nmap 7.99 ( https://nmap.org ) at 2026-06-22 22:29 +0500
Nmap scan report for 192.168.100.1
Host is up (0.0097s latency).
Not shown: 995 closed tcp ports (reset)

PORT   STATE     SERVICE  VERSION
21/tcp filtered  ftp
22/tcp filtered  ssh
23/tcp filtered  telnet
53/tcp open      domain   (generic dns response: NOTIMP)
80/tcp open      ssl/http

MAC Address: E8:13:6E:3D:E6:B1 (Huawei Technologies)
```

---

## 🔍 Breaking Down the Scan Results

### Host Status

```text
Host is up (0.0097s latency)
```

* The target device is reachable.
* Response time is approximately **9.7 ms**.

---

### Closed Ports

```text
Not shown: 995 closed tcp ports (reset)
```

* Nmap scanned 1000 common ports.
* 995 ports responded with a reset packet, meaning they are closed.

---

### Port 21 - FTP

```text
21/tcp filtered ftp
```

* **Protocol:** FTP
* **State:** Filtered
* Firewall is preventing access to the FTP service.

---

### Port 22 - SSH

```text
22/tcp filtered ssh
```

* **Protocol:** SSH
* **State:** Filtered
* Remote management access is protected by filtering.

---

### Port 23 - Telnet

```text
23/tcp filtered telnet
```

* **Protocol:** Telnet
* **State:** Filtered
* Telnet is insecure, and filtering helps improve security.

---

### Port 53 - DNS

```text
53/tcp open domain
```

* **Protocol:** DNS
* **State:** Open
* Responsible for resolving domain names into IP addresses.

---

### Port 80 - HTTP

```text
80/tcp open ssl/http
```

* **Protocol:** HTTP
* **State:** Open
* Likely provides access to the router's web interface.

---

### MAC Address Information

```text
MAC Address: E8:13:6E:3D:E6:B1 (Huawei Technologies)
```

This reveals:

* Manufacturer: **Huawei Technologies**
* Hardware identifier of the network device.

---

## 🧠 Key Takeaways

* Ports are communication endpoints.
* Port states reveal how accessible services are.
* TCP uses a three-way handshake for reliable communication.
* Nmap can identify services and their versions.
* Firewalls commonly filter sensitive ports to reduce attack surfaces.
* Open ports provide information about running services.

---

## 🧰 Tools Used

* Kali Linux
* Nmap 7.99
* Local Gateway Router (Huawei)

---

## ✅ Day 6 Complete

### Learned

* ✔ Network ports and states
* ✔ Common protocols and services
* ✔ TCP 3-Way Handshake
* ✔ Service discovery with Nmap
* ✔ Basic reconnaissance concepts

---

> *"Understanding ports and services is the foundation of network reconnaissance and cybersecurity."*
