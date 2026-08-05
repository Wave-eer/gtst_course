# Linux, the Kernel, and the Shell

## 1. Linux Is a Kernel, Not an Operating System

This is the key distinction to understand first: **Linux by itself is a kernel, not a full operating system.**

## 2. What Is a Kernel?

A **kernel** is the core piece of code/program that lets **hardware and software communicate**. It manages memory, processes, and devices, acting as the translator between the physical machine and the programs running on it.

## 3. When Does Linux Become an Operating System?

Linux only becomes a full operating system once it's paired with additional software (like GNU tools) that let users actually interact with the system — this is covered in the history below.

## 4. History of Linux

### Unix (1969)

- Originated in **1969** at Bell Labs, created by two computer scientists: **Ken Thompson and Dennis Ritchie**.
- Built using a **PDP-7** computer.
- Drawbacks of Unix compared to modern systems:
    1. **Expensive** — it was a commercial, licensed product.
    2. **Not open source** — the source code was not available for everyone to view or modify.

### GNU Project (1983)

- In **1983**, **Richard Stallman** created the **GNU Project**.
- GNU aimed to be a free, open-source **software replacement for Unix**.
- However, GNU was only a collection of software/tools — it was **not a complete operating system**, because it still lacked a kernel.

### The Linux Kernel (1991)

- Years later, a university student named **Linus Torvalds** developed the **Linux kernel**, written in the **C programming language**.
- Unlike Unix, it was released as **open source** — anyone could access and modify the code.

### GNU + Linux = A Complete OS

- On its own, the Linux kernel isn't an operating system — it needs supporting software to let users actually do things with it.
- Combining the **Linux kernel** with the **GNU software tools** created a complete, usable operating system: **GNU/Linux**.

# What Is a Shell?

The **shell** is the program that lets a user communicate with the **kernel** (the core of the operating system). It's a **Command Line Interpreter (CLI)** — it takes the commands you type, interprets them, and translates them into something the kernel can execute.

## Types of Shell

| Shell | Description |
|-------|-------------|
| **sh** | The original, most basic shell (Bourne Shell). Very limited — for example, you can't easily move the cursor around on a line while typing. It's minimal and mostly used in scripting or constrained environments (popular in lightweight/embedded systems and CTF-style challenges because of its bare-bones nature). |
| **bash** | (Bourne Again Shell) The most common default shell on Linux. Supports command coloring and **tab-completion** (auto-completing commands/paths). |
| **zsh** | Similar to bash but with a more advanced and customizable **completion** system, plus extra features like better theming (e.g., via Oh My Zsh). |
| **fish** | (Friendly Interactive Shell) Known for being very colorful out of the box, with smart, user-friendly autosuggestions and command completion — but it's less POSIX-compliant, so some bash scripts won't run in it directly. |

Shells mainly differ in things like: **syntax coloring, piping behavior, and command auto-completion**.

To check which shell you're currently using:

\```bash
echo $SHELL
\```

---

# What Is an Operating System?

The **operating system (OS)** is the core software that lets you actually *use* the computer — it manages hardware and lets other software run (you really notice its importance when it crashes or you "lose it"!).

An OS is generally made up of:
- **Kernel** – the core that talks directly to hardware
- **Software** – applications that run on top of the OS
- **Desktop Environment (DE)** – the graphical interface
- **File system/extensions** – how files are organized and named
- **Window Manager** – handles how windows are displayed, moved, resized

> **Note:** Windows' kernel is closed-source (proprietary), while the **Linux kernel is open-source** — meaning anyone can view, modify, and redistribute its code.

---

## 3. Desktop Environment (DE)

A **Desktop Environment** is the graphical layer that gives users a visual way to interact with the OS (icons, windows, menus, taskbars) instead of just a command line.

### Common Linux Desktop Environments

- **MATE** – Lightweight and functional, but not very visually polished.
- **GNOME** – Known for smooth, modern animations and a clean look; but this visual polish costs more system resources.
- **KDE Plasma** – Highly customizable, and its layout feels similar to Windows 10, making it comfortable for switchers.
- **XFCE** – Lightweight and fast, though simpler in appearance.

### Which Desktop Environment Is "Best"?

It depends on what you're optimizing for:

- **Animations & visual effects** → GNOME or KDE Plasma
- **High performance / low resource usage** → XFCE (and to a lesser extent, MATE)
- **Balance of features and speed** → KDE Plasma is often considered a strong middle ground

**Summary:** If you want eye candy and modern design, go with **GNOME** or **KDE Plasma**. If you want **speed and lower resource usage** (e.g., on an older machine), go with **XFCE**.

---

## 4. Window Manager

The **Window Manager (WM)** controls how windows are displayed, positioned, and interacted with on screen — things like borders, resizing, moving, and switching between open windows.

- In Linux, one popular window manager is **i3** (a _tiling_ window manager).
    - It's keyboard-driven — you use shortcuts instead of relying on the mouse/cursor.
    - It automatically **splits the screen** when you open multiple windows, arranging them in tiles rather than overlapping stacks.

---

## 5. Why Linux?

- Linux scales well across both **high-performance** and **low-resource** systems, making it fast and versatile.
- It's widely used across the industry:
    - **47%** of developers use Linux
    - **85%** of smartphones run a Linux-based OS (Android)
    - **96.3%** of the top servers in the world run Linux
- Most **hacking/penetration-testing tools** are Linux-based (built for and run best on Linux).
- Considered **more secure**, generally because:
    - Most **malware** is developed to target **Windows**, since it's the more common consumer OS.
    - Windows is controlled by Microsoft, meaning your system relies on a closed, centrally-managed company — raising more privacy/data concerns for some, especially in high-stakes situations like security research.

---

## 6. Linux Distributions (Distros)

A **Linux distribution** is essentially a customized package/bundle built around:

- Linux **Kernel**
- **Packages** (often GNU tools)
- **Package Manager**
- **Desktop UI**

### Distro Families

**Debian-based:**

- Kali Linux
- Ubuntu
- Parrot OS

**Arch-based:**

- BlackArch
- Garuda

### For Hackers/Security Work

|Distro|Focus|
|---|---|
|**Kali Linux**|Comes pre-loaded with almost all penetration-testing/security tools.|
|**Parrot OS**|Lets you choose between a "developer" setup or a "security/hacking" setup.|
|**Ubuntu**|A blank-ish slate — you customize it yourself to add whatever tools you need.|

#### Kali Linux

- Designed for **digital forensics** and **penetration testing**.
- Funded/maintained by **Offensive Security**.
- Package manager: `apt`
- Default shell: `zsh`
- Desktop environment: `XFCE`

#### Parrot OS

- Focused on **security, privacy, and development**.

#### Ubuntu

- Package manager: `apt`
- Default shell: `bash`

---

## 7. Do Windows Have Distros?

**No.** Since Windows is **closed-source (proprietary)**, users/developers can't modify and redistribute it the way they can with Linux — so there's no equivalent concept of "Windows distros."
## 8  How Can We Use Linux?


[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#how-can-we-use-linux)

## 1. Main OS (Main Boot)

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#1-main-os-main-boot)

Linux is installed as the only operating system.

### Advantages

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#advantages)

- Better Performance
- Simple Setup
- More Secure

### Disadvantages


- No access to another operating system.
- Risk of data loss during installation.

---

## 2. Dual Boot (2-in-1)

Linux is installed alongside Windows (or another operating system).

### Advantages

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#advantages-1)

- Access to multiple operating systems.
- Better hardware performance than virtual machines.

### Disadvantages

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#disadvantages-1)

- Installation is more complex.
- Storage is shared.

---

## 3. Live Boot

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#3-live-boot)

Run Linux directly from a USB drive or DVD without installing it.

### Advantages

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#advantages-2)

- Better privacy.
- No risk of data loss.
- No installation required.

### Disadvantages

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#disadvantages-2)

- Shared system resources.
- Usually slower than an installed system.

---

## 4. Cloud Terminals

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#4-cloud-terminals)

You can practice Linux online without installing it.

- [https://www.webminal.org](https://www.webminal.org)
- [https://shell.cloud.google.com/?show=ide,terminal](https://shell.cloud.google.com/?show=ide,terminal)

---

## 5. Virtual Machine (VM)


Modern computers support **Virtualization**, allowing multiple operating systems to run on one computer.

### Types of Virtualization


### Type 1 Hypervisor (Bare-Metal)


Runs directly on physical hardware.

Examples:

- VMware ESXi
- Proxmox
- Xen

Advantages:

- High performance
- Better resource management
- Better isolation
- Common in enterprise environments

---

### Type 2 Hypervisor (Hosted)

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#type-2-hypervisor-hosted)

Runs on top of an existing operating system.

Examples:

- VMware Workstation
- Oracle VirtualBox

Advantages:

- Easy to install
- Suitable for learning and development

---

## 6. WSL v2 (Windows Subsystem for Linux)

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#6-wsl-v2-windows-subsystem-for-linux)

Allows Linux to run inside Windows.

### Installation

[](https://github.com/innovatorsemir/gtst_course/blob/main/Day2_Linux.md#installation)

Open **Windows PowerShell (Run as Administrator)**

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

Or simply install **Ubuntu**, **Kali Linux**, or another Linux distribution from the **Microsoft Store**.

---

## 7. Termux (Android)


Termux is an Android application that provides a Linux terminal.

It is useful for:

- Running Linux commands
- Programming
- Learning Bash
- Practicing simple Linux tasks


| Term                    | What It Is                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------ |
| **Kernel**              | Core program that lets hardware and software communicate                                         |
| **Unix (1969)**         | Original OS by Ken Thompson & Dennis Ritchie — expensive, closed-source                          |
| **GNU (1983)**          | Richard Stallman's free/open-source software replacement for Unix — software only, not a full OS |
| **Linux Kernel (1991)** | Open-source kernel created by Linus Torvalds in C                                                |
| **GNU/Linux**           | Linux kernel + GNU software = complete operating system                                          |
| **Shell**               | CLI that interprets user commands into a format the kernel understands                           |