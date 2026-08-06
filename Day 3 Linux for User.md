# Kali Linux Overview & Linux Command Fundamentals

## 1. Introduction to Kali Linux

**Kali Linux** is a Debian-based Linux distribution purpose-built for penetration testing, digital forensics, and security auditing. It was previously known as **BackTrack Linux** before being rebuilt and rebranded by Offensive Security.

### Desktop Environment

This course demonstrates Kali Linux using the **GNOME Desktop Environment**, though the distribution supports multiple alternatives that can be selected based on personal preference or system resource constraints:

|Desktop Environment|Characteristics|
|---|---|
|**GNOME**|Modern, feature-rich, higher resource usage|
|**KDE Plasma**|Highly customizable, visually polished|
|**XFCE**|Lightweight, fast, ideal for lower-spec machines|
|**MATE**|Traditional desktop layout, moderate resource usage|

Users can switch between desktop environments post-installation depending on workflow needs.

---

## 2. Kali Linux Tool Categories

Kali Linux ships with hundreds of pre-installed security tools, organized into functional categories accessible from the applications menu. Below is a categorized breakdown with representative tools for each.

### 2.1 Information Gathering

Tools used to collect intelligence about target systems, networks, domains, and hosts (reconnaissance phase).

|Tool|Purpose|
|---|---|
|dmitry|Domain/IP information gathering|
|ike-scan|IPsec VPN scanning|
|legion|Automated reconnaissance and scanning|
|maltego|Link-analysis and OSINT visualization|
|netdiscover|Active/passive ARP-based network discovery|
|nmap|Network mapping and port scanning|
|p0f|Passive OS fingerprinting|
|recon-ng|Web-based reconnaissance framework|
|spiderfoot|Automated OSINT collection|

### 2.2 Vulnerability Analysis

Tools used to identify known weaknesses in systems and networks.

|Tool|Purpose|
|---|---|
|legion|Automated vulnerability scanning|
|lynis|System security auditing|
|nikto|Web server vulnerability scanning|
|nmap|Vulnerability scripting engine (NSE)|
|unix-privesc-check|Privilege escalation vector detection|

### 2.3 Web Application Analysis

Tools used to discover vulnerabilities and exploitable flaws in web applications.

|Tool|Purpose|
|---|---|
|Burp Suite|Web application security testing platform|
|commix|Command injection exploitation|
|httrack|Website mirroring/cloning|
|paros|Web proxy and vulnerability scanner|
|skipfish|Automated web application scanner|
|sqlmap|Automated SQL injection testing|
|webscarab|Web application security testing framework|
|WPScan|WordPress vulnerability scanner|
|OWASP ZAP|Web app security scanner|

### 2.4 Database Assessment

Tools focused on identifying vulnerabilities in database systems.

|Tool|Purpose|
|---|---|
|sqlmap|SQL injection detection/exploitation|
|jSQL Injection|Java-based SQL injection tool|

### 2.5 Password Attacks

Tools used for password auditing, cracking, and recovery.

|Tool|Purpose|
|---|---|
|CeWL|Custom wordlist generation from websites|
|Crunch|Wordlist generator|
|Hydra|Online password brute-forcing|
|John the Ripper|Offline password cracking|
|Hashcat|GPU-accelerated password cracking|

### 2.6 Wireless Attacks

Tools for assessing wireless network security.

|Tool|Purpose|
|---|---|
|Aircrack-ng|Wi-Fi security auditing suite|
|Kismet|Wireless network detector/sniffer|
|Wifite|Automated wireless attack tool|
|Reaver|WPS brute-force attacks|
|Bully|WPS attack tool|

### 2.7 Reverse Engineering

Tools for analyzing software, binaries, and mobile applications.

|Tool|Purpose|
|---|---|
|apktool|Android APK decompilation|
|Ghidra|Software reverse engineering suite|
|radare2|Binary analysis framework|
|jadx|Android DEX-to-Java decompiler|

### 2.8 Exploitation Tools

Tools used to exploit identified vulnerabilities.

|Tool|Purpose|
|---|---|
|Metasploit Framework|Exploit development and delivery platform|
|Searchsploit|Local Exploit-DB search utility|
|BeEF|Browser exploitation framework|

### 2.9 Sniffing & Spoofing

Tools used to capture, analyze, and manipulate network traffic.

|Tool|Purpose|
|---|---|
|Wireshark|Network protocol analyzer|
|Ettercap|Man-in-the-middle attack suite|
|Bettercap|Network attack and monitoring framework|
|Tcpdump|Command-line packet analyzer|

### 2.10 Post Exploitation

Tools used after gaining initial access to maintain and extend control over a target.

|Tool|Purpose|
|---|---|
|PowerSploit|PowerShell post-exploitation framework|
|Empire|Post-exploitation C2 framework|
|Backdoor Factory|Backdoor injection into executables|

### 2.11 Forensics

Tools for digital forensic investigation and evidence analysis.

|Tool|Purpose|
|---|---|
|Autopsy|Digital forensics platform|
|Foremost|File carving/recovery|
|Binwalk|Firmware analysis and extraction|
|Volatility|Memory forensics framework|

### 2.12 Reporting Tools

Tools used for documentation and report preparation.

|Tool|Purpose|
|---|---|
|Dradis|Collaborative reporting platform|
|CherryTree|Hierarchical note-taking|
|Maltego|Visual reporting and link analysis|

### 2.13 Social Engineering Tools

Tools used to simulate social engineering attacks for security awareness testing.

|Tool|Purpose|
|---|---|
|Social Engineering Toolkit (SET)|Social engineering attack simulation|
|BeEF|Browser-based social engineering vector|

### 2.14 System Services

Kali provides service-management commands for starting and stopping bundled tools that run as background services.

```bash
# BeEF (Browser Exploitation Framework)
beef-xss start
beef-xss stop

# Dradis (Reporting Platform)
dradis start
dradis stop
```

### 2.15 Commonly Used Applications

Everyday productivity applications included in Kali Linux.

|Application|Purpose|
|---|---|
|Firefox|Web browser|
|Terminal|Command-line access|
|Text Editor|Basic text editing|
|File Manager|Filesystem navigation|
|VS Code|Code editor / IDE|
|LibreOffice|Office productivity suite|

---

## 3. The Linux Shell

The **shell** is the interface layer between the user and the Linux kernel. It interprets user commands and passes them to the kernel for execution.

```
User
  │
  ▼
Shell
  │
  ▼
Kernel
  │
  ▼
Hardware
```

### Popular Linux Shells

|Shell|Notes|
|---|---|
|**bash** (Bourne Again Shell)|Most common default shell|
|**zsh** (Z Shell)|Highly configurable, popular with plugin frameworks|
|**fish** (Friendly Interactive Shell)|User-friendly, auto-suggestions built in|
|**sh** (Bourne Shell)|POSIX-standard, lightweight|

### Checking the Current Shell

```bash
echo $SHELL
```

---

## 4. Anatomy of a Linux Terminal Prompt

A standard Linux terminal prompt is composed of five distinct parts:

```
rexder@HunterMachine:~/Documents$
```

|#|Component|Example|Description|
|---|---|---|---|
|1|**Username**|`rexder`|The currently logged-in user|
|2|**Hostname**|`HunterMachine`|The machine's network name|
|3|**Current Directory**|`~/Documents`|The active working directory|
|4|**Privilege Symbol**|`$` or `#`|`$` = standard user, `#` = root/administrator|
|5|**Command Area**|_(cursor position)_|Where commands are typed and executed|

---

## 5. Essential Linux Commands

### 5.1 `pwd` — Print Working Directory

**Synopsis**

```bash
pwd [options]
```

**Description** Displays the absolute path of the current working directory, measured from the filesystem root (`/`).

**Example**

```bash
pwd
```

**Output**

```
/home/rexder/Documents
```

---

### 5.2 `cd` — Change Directory

**Synopsis**

```bash
cd [directory]
```

**Description** Changes the shell's current working directory.

**Common Usage Patterns**

|Command|Result|
|---|---|
|`cd /`|Navigate to the filesystem root|
|`cd`|Return to the current user's home directory|
|`cd ..`|Move up one directory level|
|`cd ../..`|Move up two directory levels|
|`cd Downloads`|Enter the "Downloads" subdirectory|
|`cd "Folder Name"`|Enter a directory whose name contains spaces (quotes required)|

---

### 5.3 `ls` — List Directory Contents

**Description** Displays the files and subdirectories contained within a directory.

**Basic Usage**

```bash
ls
```

**Useful Options**

|Command|Description|
|---|---|
|`ls -l`|Long-format listing (permissions, owner, size, date)|
|`ls -a`|Show hidden files (files beginning with `.`)|
|`ls filename`|List a specific file or directory|
|`ls -R`|List directory contents recursively|
|`ls -Rla` or `ls -la`|Combine multiple options|

> **Note:** Hidden files in Linux are prefixed with a dot (`.`), for example: `.bashrc`, `.profile`, `.cache`, `.config`.

---

### 5.4 `tree` — Directory Tree Structure

**Description** Displays the contents of a directory as a visual, hierarchical tree.

**Example**

```bash
tree
```

**Output**

```
.
├── Documents
├── Downloads
├── Music
├── Pictures
└── Videos
```

---

## 6. Chaining and Combining Commands

Linux allows multiple commands to be executed on a single line using control operators.

|Operator|Behavior|Example|
|---|---|---|
|`;`|Runs commands sequentially, regardless of success/failure|`pwd ; ls ; whoami`|
|`&&`|Runs the next command **only if** the previous command succeeds|`mkdir test && cd test`|
|`\|`|Runs the next command **only if** the previous command fails|`mkdir test \| echo "Folder already exists"`|

---

## 7. Text Manipulation Utilities

Linux provides a comprehensive set of command-line utilities for viewing, editing, filtering, and transforming text data.

|Command|Function|
|---|---|
|`cat`|Display file contents|
|`less` / `more`|View file contents page-by-page|
|`head`|Display the first lines of a file|
|`tail`|Display the last lines of a file|
|`nano`|Beginner-friendly terminal text editor|
|`vim`|Advanced modal terminal text editor|
|`grep`|Search for text patterns|
|`sort`|Sort lines of text|
|`uniq`|Filter/report repeated lines|
|`cut`|Extract sections from each line|
|`tr`|Translate or delete characters|
|`sed`|Stream editor for filtering/transforming text|
|`awk`|Pattern scanning and text processing language|

**Core capabilities enabled by these tools:**

- Viewing and paginating file contents
- Editing text directly in the terminal
- Searching for specific patterns within files
- Performing find-and-replace operations
- Filtering and reformatting command output
- Efficiently processing large text files

---
