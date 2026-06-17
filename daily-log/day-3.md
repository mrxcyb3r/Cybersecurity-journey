# 🟢 Day 3: The Linux Foundation (Identity, Access, & Power)

**Date:** June 17, 2026  
**Focus:** Full Command Reference & Linux Workflow.

---

## 🛠️ The Cybersecurity Researcher's Command Reference

### 1. Navigation & Inspection
* **`ls -alF`**: Detailed directory listing (shows hidden files and types).
* **`cd [path]`**: Move between directories.
* **`pwd`**: Confirm your current location in the file system.
* **`find / -name [name] 2>/dev/null`**: Search for files across the entire system; silences "Permission Denied" errors.

### 2. Searching & Data Processing (The "Pipes")
* **`grep -rn "keyword" /path`**: Recursive search for a string/pattern within files.
* **`cat [file]`**: Print entire file contents to the terminal.
* **`less [file]`**: Read large files page-by-page.
* **`|` (Pipe)**: Redirects output. *Example:* `ps aux | grep root` (filters process list for root-owned tasks).

### 3. Identity & Permissions
* **`id`**: Shows your current UID and GID.
* **`whoami`**: Returns current username.
* **`sudo -l`**: Lists commands available to your user with elevated privileges.
* **`chmod [mode] [file]`**: Modify file/directory access.
    * `700`: Private (Owner only).
    * `755`: Standard (Public Read/Execute).
    * `600`: Sensitive Data (Private).
* **`chown [user]:[group] [file]`**: Change file ownership.

### 4. Network & Process Intelligence
* **`ss -tulpn`**: The security audit tool; lists all listening ports and their associated processes.
* **`ps auxf`**: Display the system process tree to identify parent/child relationships.
* **`kill -9 [PID]`**: Forcefully terminate a process using its Process ID.
* **`top` / `htop`**: Real-time system resource monitor.

### 5. System Reconnaissance
* **`which [command]`**: Locate the absolute path of a binary.
* **`uname -a`**: View kernel information (critical for OS-level exploit discovery).
* **`ip addr`**: Display current network interface settings.

---

## 💀 The "Researcher's Workflow" Logic
When analyzing a system for vulnerabilities, professional operators chain these commands:
1. **`ss -tulpn`**: Identify open "doors" (ports).
2. **`ps aux | grep [PID]`**: Discover what program is guarding those doors.
3. **`ls -l [path]`**: Verify if that program is running with `root` privileges.



---

## 📝 Learning Summary
I have documented the essential Linux toolkit. I can now navigate, audit system processes, manipulate permissions (using octal math), and utilize pipes to filter system data. I am prepared to move into script-based automation.
