# 🐍 Day 3 - Python for Cybersecurity Practice

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Learning-green)
![Status](https://img.shields.io/badge/Day-3-success)

---

# 🎯 Objective

Today was dedicated to practicing the Python concepts learned during Day 2.

The focus was on:

* Loops
* Conditional Statements
* String Methods
* Dictionaries
* Sets
* List Comprehensions

These concepts are fundamental for automating cybersecurity tasks such as log analysis, threat detection, vulnerability assessment, and data processing.

---

# 📈 Progress

| Day   | Topic                     | Status |
| ----- | ------------------------- | ------ |
| Day 1 | Python Fundamentals       | ✅      |
| Day 2 | Data Structures & Methods | ✅      |
| Day 3 | Practice & Reinforcement  | ✅      |

---

# 📝 Task 1: Port Classification

### Challenge

```python
ports = [22, 80, 443, 21, 3389, 8080, 3306]

# Print "Open" if port is 22, 80, or 443
# Print "High Risk" if port is 3389 or 21
# Print "Normal" for others
```

<details>
<summary>💡 View Solution</summary>

```python
ports = [22, 80, 443, 21, 3389, 8080, 3306]

for port in ports:
    if port in [22, 80, 443]:
        print(f"{port} → Open")
    elif port in [21, 3389]:
        print(f"{port} → High Risk")
    else:
        print(f"{port} → Normal")
```

</details>

---

# 📝 Task 2: Counting Login Attempts

### Challenge

```python
attempts = [3, 8, 1, 5, 12, 0, 7]

# Count attempts greater than 5
# Print warning if attempts exceed 10
```

<details>
<summary>💡 View Solution</summary>

```python
attempts = [3, 8, 1, 5, 12, 0, 7]

count_greater_5 = 0

for attempt in attempts:
    if attempt > 5:
        count_greater_5 += 1

    if attempt > 10:
        print(f"Brute Force Possible for {attempt} attempts")

print("Total attempts > 5:", count_greater_5)
```

</details>

---

# 📝 Task 3: Log Parsing with split()

### Challenge

```python
log = "192.168.1.100 - FAILED - SSH - 2025-06-25"

# Extract IP, Status, Service and Date
```

<details>
<summary>💡 View Solution</summary>

```python
log = "192.168.1.100 - FAILED - SSH - 2025-06-25"

parts = log.split(" - ")

ip = parts[0]
status = parts[1]
service = parts[2]
date = parts[3]

print(ip)
print(status)
print(service)
print(date)
```

</details>

---

# 📝 Task 4: Extract IP Addresses from Logs

### Challenge

```python
logs = [
    "User admin logged in from 10.0.0.5",
    "Failed login attempt from 192.168.1.20",
    "User root connected from 172.16.0.1"
]

# Extract IP addresses
```

<details>
<summary>💡 View Solution</summary>

```python
logs = [
    "User admin logged in from 10.0.0.5",
    "Failed login attempt from 192.168.1.20",
    "User root connected from 172.16.0.1"
]

for line in logs:
    parts = line.split()

    for word in parts:
        if word.count('.') == 3:
            print(word)
            break
```

</details>

---

# 📝 Task 5: Working with Dictionaries

### Challenge

```python
scan_result = {
    "target": "192.168.1.10",
    "ports": [22, 80, 443],
    "os": "Windows",
    "vulnerable": True
}
```

<details>
<summary>💡 View Solution</summary>

```python
scan_result = {
    "target": "192.168.1.10",
    "ports": [22, 80, 443],
    "os": "Windows",
    "vulnerable": True
}

print("OS:", scan_result["os"])

if scan_result["vulnerable"]:
    print("Warning: Target is vulnerable!")

scan_result["scan_date"] = "2025-06-25"

print("Scan Date:", scan_result["scan_date"])
```

</details>

---

# 📝 Task 6: Working with Sets

### Challenge

```python
scanned_ips = {"192.168.1.10", "10.0.0.5", "192.168.1.10", "172.16.0.1"}

new_ips = [
    "192.168.1.20",
    "10.0.0.5",
    "192.168.1.30"
]
```

<details>
<summary>💡 View Solution</summary>

```python
scanned_ips = {"192.168.1.10", "10.0.0.5", "192.168.1.10", "172.16.0.1"}

new_ips = [
    "192.168.1.20",
    "10.0.0.5",
    "192.168.1.30"
]

scanned_ips.update(new_ips)

print(scanned_ips)

failed_ips = {
    "192.168.1.10",
    "172.16.0.1",
    "10.0.0.5"
}

blocked_ips = {
    "10.0.0.5",
    "192.168.1.50"
}

common = failed_ips & blocked_ips
all_ips = failed_ips | blocked_ips

print(common)
print(all_ips)
```

</details>

---

# 📝 Task 7: List Comprehensions

### Challenge

```python
ports = [22, 80, 443, 21, 3389, 8080, 25, 110]

# Extract:
# Even ports
# Ports greater than 100
```

<details>
<summary>💡 View Solution</summary>

```python
ports = [22, 80, 443, 21, 3389, 8080, 25, 110]

even_ports = [p for p in ports if p % 2 == 0]
high_ports = [p for p in ports if p > 100]

print(even_ports)
print(high_ports)
```

</details>

### Challenge 2

```python
logs = [
    "192.168.1.10 FAILED",
    "10.0.0.5 SUCCESS",
    "192.168.1.20 FAILED",
    "172.16.0.1 SUCCESS"
]

# Extract failed login IPs
```

<details>
<summary>💡 View Solution</summary>

```python
logs = [
    "192.168.1.10 FAILED",
    "10.0.0.5 SUCCESS",
    "192.168.1.20 FAILED",
    "172.16.0.1 SUCCESS"
]

failed_ips = [
    log.split()[0]
    for log in logs
    if "FAILED" in log
]

print(failed_ips)
```

</details>

---

# 🧠 Key Concepts Reinforced

### Loops

```python
for item in collection:
    pass
```

Used for iterating through logs, ports, and security events.

---

### String Splitting

```python
log.split()
```

Useful for parsing:

* Log files
* Network traffic
* Command output

---

### Dictionaries

```python
data["key"]
```

Useful for:

* Scan results
* API responses
* Security reports

---

### Sets

```python
set1 & set2
set1 | set2
```

Useful for:

* Finding common attackers
* Removing duplicates
* Comparing threat intelligence feeds

---

### List Comprehensions

```python
[item for item in data if condition]
```

Useful for quickly filtering:

* IP addresses
* Ports
* Log entries
* Users

---

## 🔥 Day 3 Complete

Today strengthened my understanding of Python data structures and core methods by solving practical cybersecurity-focused exercises involving ports, logs, IP addresses, and vulnerability data.
