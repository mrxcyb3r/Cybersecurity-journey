# 🐧 Day 12 — Linux fundamentals

> *Today's focus was mastering Linux navigation, understanding the Linux filesystem hierarchy, and learning how to create, organize, move, copy, and manage files directly from the command line. These are essential skills for every cybersecurity professional and penetration tester.*

---

<div align="center">

## 📅 Day 12

**Module:** Linux Fundamentals (Hack The Box)

**Status:** ✅ Completed

</div>

---

# 🎯 Objectives

* Understand Linux architecture and philosophy
* Learn the Linux File System Hierarchy (FHS)
* Navigate the filesystem efficiently
* Inspect files and directories
* Create and organize files and folders
* Move, rename, and copy files
* Improve productivity with shell shortcuts

---

# 🐧 Linux Structure & Philosophy

Linux follows a simple yet powerful philosophy:

* Build small tools that perform one task well
* Combine commands together to accomplish complex tasks
* Everything in Linux is treated as a file
* Configuration files are stored as plain text
* The terminal provides complete control over the operating system

### Linux Architecture

```text
Hardware
   │
   ▼
Kernel
   │
   ▼
Shell
   │
   ▼
System Utilities
```

### Components

* **Hardware** – CPU, RAM, storage devices
* **Kernel** – Manages hardware and system resources
* **Shell** – Interprets user commands
* **Utilities** – Programs used to interact with the operating system

---

# 📂 Linux File System Hierarchy (FHS)

I learned the purpose of the most important Linux directories.

| Directory | Purpose                        |
| --------- | ------------------------------ |
| `/`       | Root directory                 |
| `/bin`    | Essential user commands        |
| `/sbin`   | Administrative system commands |
| `/etc`    | Configuration files            |
| `/home`   | User home directories          |
| `/root`   | Root user's home directory     |
| `/dev`    | Device files                   |
| `/var`    | Variable data such as logs     |
| `/tmp`    | Temporary files                |

---

# 🧭 Navigation Commands

## Display Current Directory

```bash
pwd
```

Shows the current working directory.

---

## List Files

```bash
ls
```

Displays files and folders.

### Long Listing

```bash
ls -l
```

Shows:

* Permissions
* Owner
* Group
* File size
* Modification date
* File name

---

### Show Hidden Files

```bash
ls -la
```

Displays hidden files beginning with a dot (`.`).

Examples:

* `.bashrc`
* `.bash_history`
* `.profile`

---

### View Another Directory

```bash
ls -l /var
```

Lists another directory without changing into it.

---

# 📁 Directory Navigation

Move into another directory:

```bash
cd /dev/shm
```

Return to the previous directory:

```bash
cd -
```

Move to the parent directory:

```bash
cd ..
```

---

# ⚡ Productivity Shortcuts

## Auto Completion

Press:

```text
TAB
```

or

```text
TAB TAB
```

to complete commands or display possible matches.

---

## Command Chaining

```bash
cd /dev/shm && clear
```

Runs the second command only if the first succeeds.

---

## Clear Terminal

```bash
clear
```

or

```text
Ctrl + L
```

---

## Search Command History

```text
Ctrl + R
```

Search previously executed commands instantly.

---

# 📄 Understanding `ls -l`

Example:

```text
drwxr-xr-x 2 user group 4096 Nov 13 Desktop
```

Meaning:

| Field       | Description            |
| ----------- | ---------------------- |
| `d`         | Directory              |
| `rwxr-xr-x` | File permissions       |
| `2`         | Number of hard links   |
| `user`      | Owner                  |
| `group`     | Group owner            |
| `4096`      | File size              |
| `Nov 13`    | Last modified date     |
| `Desktop`   | File or directory name |

---

# 📂 Working with Files & Directories

Unlike Windows, Linux allows users to efficiently create, edit, move, and manage files directly from the terminal. This command-line approach is faster, easier to automate, and essential for system administration and cybersecurity tasks.

---

## Creating Files

Create an empty file:

```bash
touch info.txt
```

Create a file inside another directory:

```bash
touch ./Storage/local/user/userinfo.txt
```

---

## Creating Directories

Create a directory:

```bash
mkdir Storage
```

Create nested directories automatically:

```bash
mkdir -p Storage/local/user/documents
```

---

## Viewing Directory Structure

Display the directory tree:

```bash
tree .
```

Example:

```text
.
├── info.txt
└── Storage
    └── local
        └── user
            └── documents
```

---

## Renaming Files

Rename a file:

```bash
mv info.txt information.txt
```

---

## Moving Files

Move multiple files into another directory:

```bash
mv information.txt readme.txt Storage/
```

---

## Copying Files

Copy a file without removing the original:

```bash
cp Storage/readme.txt Storage/local/
```

---

# 💡 Important Concepts

During today's lesson I learned that:

* `touch` creates empty files.
* `mkdir` creates directories.
* `mkdir -p` creates nested directories automatically.
* `mv` is used to move **and** rename files.
* `cp` copies files while keeping the original.
* `tree` displays the filesystem hierarchy.
* Relative paths (`.`) refer to the current directory.
* Linux file management from the terminal is faster and easier to automate than using a graphical interface.

---

# 🛠️ Commands Practiced

```bash
pwd

ls

ls -l

ls -la

ls -l /var

cd

cd ..

cd -

touch

mkdir

mkdir -p

tree

mv

cp

clear
```

---

# 🎯 Learning Outcomes

By the end of Day 12, I can:

* ✅ Explain the Linux architecture
* ✅ Understand the Linux filesystem hierarchy
* ✅ Navigate directories confidently
* ✅ Inspect files and permissions
* ✅ Create files and directories
* ✅ Create nested directory structures
* ✅ Rename files
* ✅ Move files between directories
* ✅ Copy files safely
* ✅ Use shell shortcuts for faster navigation

---

# 🛡️ Why This Matters for Cybersecurity

Linux is the foundation of penetration testing, digital forensics, cloud infrastructure, and system administration. Every security professional must know how to efficiently navigate the filesystem, manage files, and work entirely from the command line. These skills are essential for tasks such as log analysis, evidence collection, automation, reconnaissance, and privilege escalation.

---

# 💭 Reflection

> *Today I became much more comfortable working in the Linux terminal. I learned how to navigate the filesystem, inspect directories, and manage files using only command-line tools. These fundamental skills are the building blocks for more advanced Linux administration and cybersecurity techniques.*

---

<div align="center">

# ✅ Day 12 Completed

**Cybersecurity Journey Progress**

🐧 Linux Fundamentals • Filesystem • Navigation • File Management

*"Mastering the Linux terminal is the first step toward mastering cybersecurity."*

</div>
