<div align="center">

# 🐍 Python for Cybersecurity Journey

# 📅 Day 8 — Building a Port Scanner with Sockets

**📆 Date:** July 1, 2026
**🎯 Focus:** Python for cybersecurity port scanner
**✅ Status:** Completed


</div>

---

## 🎯 Focus & Objectives

The goal today was to pivot from pure network theory to practical application. I learned how to use Python's native **sockets** module to interface directly with network ports and build a functional, lightweight TCP port scanner from scratch.

---

## 🔰 Core Concepts: Understanding Socket Syntax

A network socket is an endpoint for sending or receiving data across a computer network. In Python, this behavior is managed using the built-in `socket` library.

```python
import socket

# Creating a socket (most important line)
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Key Parameters:
# - socket.AF_INET    → Directs the socket to use the IPv4 addressing family.
# - socket.SOCK_STREAM → Configures the socket to use TCP (Transmission Control Protocol),
#                         which relies on a reliable connection handshake.

```

### The Connection Lifecycle Flow:

1. **Instantiation:** Create the socket instance.
2. **Timeout Configuration:** Set a maximum wait time so the application does not hang indefinitely on non-responsive ports.
3. **Execution (`connect_ex`):** Attempt the connection. `connect_ex()` returns an error indicator (`0` if the connection succeeds, or a specific error number if it fails) instead of raising an immediate runtime exception.
4. **Cleanup:** Always release the socket resource by closing it.

```python
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  # Create socket
sock.settimeout(1)                                        # Set timeout (seconds)
result = sock.connect_ex((ip, port))                      # Test connection
sock.close()                                              # Terminate connection

```

---

## 🛠 Project: Simple Port Scanner (`port_scanner.py`)

This application maps out network hosts by systematically probing common ports to verify active network services.

```python
import socket   # Module used for network connections
import time     # To calculate how long the scan takes

# Map of common operational ports and their corresponding protocol services
port_names = {
    21: "FTP",       # File Transfer Protocol
    22: "SSH",       # Secure Shell (Remote Login)
    23: "Telnet",    # Legacy cleartext remote access
    25: "SMTP",      # Simple Mail Transfer Protocol
    53: "DNS",       # Domain Name System
    80: "HTTP",      # Hypertext Transfer Protocol (Web)
    443: "HTTPS",    # Encrypted Secure Web traffic
    3306: "MySQL",   # Relational Database
    5432: "PostgreSQL",
    8080: "HTTP-Alt" # Common secondary alternative web port
}

def scan_port(ip, port):
    """
    Attempts a raw TCP handshake with a target IP and port.
    Returns True if the port accepts the connection, False otherwise.
    """
    try:
        # Step 1: Initializing the network socket
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        
        # Step 2: Enforcing a strict 1-second operational timeout
        sock.settimeout(1)
        
        # Step 3: Probing the network socket address tuple
        result = sock.connect_ex((ip, port))
        
        # Step 4: Gracefully close resource to prevent leakage
        sock.close()
        
        # Error code 0 implies a perfectly established socket handshake
        if result == 0:
            return True
        else:
            return False
            
    except Exception:
        return False  # Catch unforeseen exceptions, falling back to a closed status


# ===================== EXECUTIVE PIPELINE =====================

if __name__ == "__main__":
    print("=== Simple Cybersecurity Port Scanner ===\n")

    # Capture the operational target parameters
    target_ip = input("Enter target IP (e.g., 127.0.0.1 or 192.168.1.1): ").strip()

    print(f"\n🔍 Initializing scan on target: {target_ip}...\n")
    print(f"{'PORT':<6} {'SERVICE':<12} STATUS")
    print("-" * 45)

    start_time = time.time()      # Record initiation epoch timestamp
    open_ports = []               # Accumulator for identified listening endpoints

    # Iterate systematically through defined dictionary services
    for port, service in port_names.items():
        if scan_port(target_ip, port):
            status = "✅ OPEN"
            open_ports.append(port)
            print(f"{port:<6} {service:<12} {status}")
        else:
            print(f"{port:<6} {service:<12} ❌ Closed")

    # Execution Analysis Summary Output
    print("\n" + "="*55)
    print(f"Scan operations concluded in {time.time() - start_time:.2f} seconds.")
    print(f"Total Open Ports Discovered: {len(open_ports)}")

    if open_ports:
        print("Open Ports List:", open_ports)
    else:
        print("Alert: No listening ports detected from the standard registry mapping.")

```

---

## 🚀 Execution & Verification

Run the utility natively using your terminal interface:

```bash
python3 port_scanner.py

```
Here is the updated section tailored to reflect your **Day 8 Port Scanner** project. It replaces your Day 7 OOP/Password Manager details with your new networking, sockets, and Python automation skills.

---

# 🎯 Skills Gained

By the end of Day 8, I can:

* ✅ Understand and instantiate Python network sockets using `socket.socket()`
* ✅ Configure socket addressing families (`AF_INET` for IPv4) and socket types (`SOCK_STREAM` for TCP)
* ✅ Implement execution connection timeouts using `settimeout()` to prevent script hanging
* ✅ Use `connect_ex()` to handle connection error codes gracefully without crashing the runtime
* ✅ Map operational ports to their respective protocol service names using Python dictionaries
* ✅ Calculate and display total script execution time using the `time` module
* ✅ Safely close network socket connections to prevent resource and file descriptor leaks
* ✅ Spin up local Netcat listeners (`nc -lvp`) to verify and test custom network script behaviors
* ✅ Apply combined Python programming logic and network theory to build a practical security tool

---

# 📂 Technologies Used

* Python 3
* Network Socket Programming (`socket` module)
* TCP/IP Suite & IPv4 Addressing
* Network Troubleshooting Tools (`netcat`)
* Resource Lifecycle Management (`sock.close()`)
* Execution Benchmarking (`time` module)

---

# 💡 Reflection

> "Today marked the bridge between network theory and practical automation. Moving away from reading about ports and protocols to actually writing a Python script that interacts with them made everything click. Building the Port Scanner taught me how sockets negotiate connections, how to handle execution timing safely with timeouts, and how `connect_ex` processes network error codes. Testing my own tool against a live Netcat listener in the terminal proved that I'm no longer just studying cybersecurity concepts—I'm building the actual tools used in the field."

---

**Day 8 Complete ✅**

*Python for Cybersecurity — Network Sockets & Port Scanning* 🐍
