🐍 Python for Cybersecurity Journey

## Day 1 - Python Basics

**Date:** June 19, 2026

Today I started learning Python fundamentals. I covered the core building blocks that are essential for programming and will be useful for cybersecurity, automation, and scripting

---

## 1. Variables & Data Types

Learned how Python stores different types of data without requiring explicit type declarations.

```python
name = "Alice"          # string
age = 25                # integer
balance = 1337.50       # float
is_hacker = True        # boolean
skills = ["Python", "Nmap", "Burp"]

ip, port = "192.168.1.1", 80
```
---

## 2. Strings & f-Strings

Learned string formatting using f-strings and common string methods.

```python
target = "192.168.1.100"
port = 445

print(f"Scanning {target}:{port} for SMB vulnerabilities")
```

### Useful String Methods

```python
target.replace("192", "10")
"admin".upper()
"password123".isalnum()
```

---

## 3. Operators

### Arithmetic Operators

```python
10 + 5
10 // 3
10 % 3
```

### Comparison Operators

```python
80 == 80
443 != 80
```

### Logical Operators

```python
if port == 22 and is_hacker:
    print("SSH access possible")
```

---

## 4. Control Structures

### If-Elif-Else

```python
if port == 22:
    print("SSH")
elif port == 80 or port == 443:
    print("Web service")
else:
    print("Other service")
```

### For Loops

```python
ports = [22, 80, 443, 3389]

for port in ports:
    print(f"Checking port {port}...")
```

### While Loops

```python
attempts = 0

while attempts < 5:
    print(f"Attempt {attempts + 1}")
    attempts += 1
```

---

## 5. Lists, Dictionaries & Sets

### Lists

```python
open_ports = [22, 80, 443]
open_ports.append(3306)
```

### Dictionaries

```python
service = {
    "port": 80,
    "name": "http",
    "vulnerable": True,
    "version": "Apache 2.4.49"
}
```

### Sets

```python
scanned = {"192.168.1.1", "192.168.1.2"}
```

Learned that sets provide fast lookups and automatically avoid duplicates.

---

## 6. Functions

Created reusable code blocks using functions.

```python
def scan_port(target, port):
    print(f"[+] Scanning {target}:{port}")
    return port in [22, 80, 443]
```

Function call:

```python
result = scan_port("10.0.0.5", 80)
print("Open" if result else "Closed")
```

Also learned about default parameters:

```python
def generate_password(length=12, use_special=True):
    pass
```

---

## 7. File Handling (Introduction)

Started learning file handling, which will be useful for:

* Saving scan results
* Writing logs
* Generating reports
* Reading wordlists

Example:

```python
# Writing
with open("scan_results.txt", "w") as f:
    f.write("Target: 192.168.1.1\n")
    f.write("Open ports: 22,80,443\n")

# Reading
with open("scan_results.txt", "r") as f:
    content = f.read()
    print(content)
```

---

## Key Takeaways

✅ Variables and data types

✅ String manipulation and f-strings

✅ Arithmetic, comparison, and logical operators

✅ Conditional statements

✅ For and while loops

✅ Lists, dictionaries, and sets

✅ Functions and parameters

✅ Basic file handling concepts

---

### Progress

Python Learning Progress: **Day 1 Completed ✅**
