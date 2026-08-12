# Linux File Hierarchy

The **Linux file system hierarchy** is the directory structure used by the operating system to organize files and directories.

Unlike Windows, which commonly uses drive letters such as `C:`, Linux uses **one main directory tree**. The top of this tree is called the **root directory**, represented by:

```bash
/
```

Linux system files and directories are organized under `/`.

> **Important:** `/` and `/root` are NOT the same thing.

There are two commonly confused meanings of "root":

1. `/` → The **root directory**, the top of the entire Linux file system.
    
2. `/root` → The **home directory of the root (administrator) user**.
    

---

## 1. `/` — Root Directory

```bash
/
```

This is the **top-level directory** of the Linux file system.

All other directories, such as `/home`, `/etc`, `/usr`, and `/var`, are located under `/`.

Example:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── root
├── sbin
├── tmp
├── usr
└── var
```

---

## 2. `/root` — Root User's Home Directory

```bash
/root
```

This is the **home directory of the root user**, which is the administrator account.

It is similar in purpose to:

```bash
/home/arsema
```

for a normal user.

For example:

```text
/home/arsema
```

→ Home directory of the user `arsema`

```text
/root
```

→ Home directory of the `root` user

The `~` symbol represents the **current user's home directory**.

For example, if you are logged in as `arsema`:

```bash
~
```

means:

```bash
/home/arsema
```

If you are logged in as root:

```bash
~
```

means:

```bash
/root
```

---

# 3. `/bin` — Essential User Binaries

```bash
/bin
```

`bin` stands for **binary**.

It contains essential executable programs/commands used by users and the system.

Examples traditionally include:

```bash
ls
cp
mv
rm
cat
grep
touch
```

> On many modern Linux distributions, `/bin` is a symbolic link to `/usr/bin`. So you may not see a separate physical collection of files in `/bin`.

---

# 4. `/boot` — Boot Files

```bash
/boot
```

This directory contains files required for the **Linux boot process**.

Examples include:

- Linux kernel
    
- Initial RAM filesystem (`initramfs`/`initrd`)
    
- Bootloader-related files
    

For example, systems using **GRUB** have GRUB-related files associated with the boot process.

The system uses these files when starting Linux.

---

# 5. `/dev` — Device Files

```bash
/dev
```

`dev` stands for **devices**.

Linux represents many hardware devices as **files** inside `/dev`.

Examples:

```text
/dev/sda
/dev/sdb
/dev/tty
/dev/null
/dev/random
```

For example:

- `/dev/sda` → commonly represents a disk
    
- `/dev/sdb` → another disk/device
    
- `/dev/null` → special device that discards data
    

> **Correction:** USB devices, RAM, and CPUs are not simply "stored" in `/dev`. Rather, Linux provides **device files/interfaces** there for interacting with hardware and kernel devices.

---

# 6. `/etc` — System Configuration Files

```bash
/etc
```

`etc` traditionally comes from **"et cetera"**, although today it is best understood as the directory containing **system-wide configuration files**.

It contains configuration files used by the operating system and many installed programs.

Examples:

```text
/etc/passwd
/etc/hosts
/etc/ssh/
/etc/fstab
```

For example:

```bash
/etc/ssh/sshd_config
```

contains configuration for the SSH server.

> `/etc` is mainly for configuration, not generally for scripts used to start and stop programs. Service management is usually handled through tools such as `systemctl`, with service definitions commonly stored under `/etc/systemd/` or other locations.

---

# 7. `/home` — Users' Home Directories

```bash
/home
```

This directory contains the **personal directories of normal users**.

Example:

```text
/home
├── arsema
├── user1
└── user2
```

A user's personal files are normally stored inside their home directory.

For example:

```bash
/home/arsema
```

contains files belonging to the user `arsema`.

The `~` symbol represents the current user's home directory.

For example:

```bash
cd ~
```

is equivalent to:

```bash
cd /home/arsema
```

when `arsema` is the current user.

---

# 8. `/lib` — Essential Shared Libraries

```bash
/lib
```

`lib` stands for **libraries**.

Libraries contain reusable code required by programs and the operating system.

For example, many Linux programs depend on shared libraries.

Shared libraries commonly have names such as:

```text
libsomething.so
```

For example:

```text
libc.so
```

> On modern Linux systems, `/lib` is often a symbolic link to `/usr/lib`.

---

# 9. `/media` — Removable Media Mount Points

```bash
/media
```

This directory is commonly used as a **mount point for removable media**.

Examples include:

- USB flash drives
    
- CDs/DVDs
    
- External storage devices
    

For example, a USB drive might be automatically mounted somewhere under:

```bash
/media/arsema/
```

The exact location depends on the Linux distribution and desktop environment.

---

# 10. `/mnt` — Temporary Mount Point

```bash
/mnt
```

This directory is traditionally used as a **temporary mount point** for manually mounted file systems.

For example, a system administrator might mount another disk with:

```bash
mount /dev/sdb1 /mnt
```

The important point is:

> `/mnt` is intended as a convenient location for temporarily mounted file systems.

It is **not true that only the root user can create files in `/mnt`**. Permissions depend on the ownership and permissions of the directory.

---

# 11. `/opt` — Optional Software

```bash
/opt
```

`opt` stands for **optional**.

It is used for installing **optional/add-on application software**, particularly software that is not part of the standard operating system installation.

For example:

```text
/opt/application/
```

An application may place its files there.

> Not all applications are installed in `/opt`. Many applications installed through a package manager use locations under `/usr`.

---

# 12. `/sbin` — System Binaries

```bash
/sbin
```

`sbin` stands for **system binaries**.

It traditionally contains programs used mainly for **system administration and maintenance**.

Examples include commands related to:

- Filesystem management
    
- Networking
    
- System administration
    

> **Important correction:** `/sbin` commands are **not necessarily commands that only root can run**. Some can be executed by normal users, although many require administrator privileges to perform certain operations.

On modern Linux systems, `/sbin` is often a symbolic link to `/usr/sbin`.

---

# 13. `/tmp` — Temporary Files

```bash
/tmp
```

This directory contains **temporary files** created by programs and users.

For example, an application may temporarily store data in:

```bash
/tmp
```

Files in `/tmp` may be deleted when the system is rebooted or according to the distribution's cleanup policies.

> Do not assume that every file in `/tmp` is guaranteed to disappear immediately after every reboot. Cleanup behavior depends on the Linux distribution and its configuration.

---

# 14. `/usr` — User Programs and Data

```bash
/usr
```

`usr` historically relates to **Unix System Resources** and contains a large portion of the system's user-space programs, libraries, documentation, and other read-only/shareable data.

Common directories include:

```text
/usr/bin
/usr/sbin
/usr/lib
/usr/share
```

For example:

```bash
/usr/bin/python
/usr/bin/grep
/usr/share/doc/
```

### Important correction

`/usr` does **not simply mean "files that are shared with other users."**

It mainly contains **user-space programs, libraries, documentation, and other system resources** that are generally shareable/read-only rather than user-specific personal files.

---

# Quick Summary

|Directory|Purpose|
|---|---|
|`/`|Root of the entire Linux file system|
|`/root`|Home directory of the root user|
|`/bin`|Essential user commands/binaries|
|`/boot`|Files needed for booting Linux|
|`/dev`|Device files/interfaces|
|`/etc`|System-wide configuration files|
|`/home`|Normal users' home directories|
|`/lib`|Essential libraries|
|`/media`|Mount points for removable media|
|`/mnt`|Temporary/manual mount point|
|`/opt`|Optional/add-on application software|
|`/sbin`|System administration binaries|
|`/tmp`|Temporary files|
|`/usr`|User-space programs, libraries, documentation, and other resources|

## The easiest way to remember them

```text
/       → Everything starts here
/root   → Root user's home
/bin    → Basic commands
/boot   → Booting
/dev    → Devices
/etc    → Configuration
/home   → Users' personal files
/lib    → Libraries
/media  → Removable media
/mnt    → Temporary mounts
/opt    → Optional software
/sbin   → System administration commands
/tmp    → Temporary files
/usr    → Programs and system resources
```


# Text Editors: Vim and Nano

## 1. Vim

### 1.1 Background

- Vim stands for **"Vi IMproved."** It is an enhanced version of the original Unix editor, **vi**.
- Historically, terminal-based editors like `vi` displayed and let users edit only **one line at a time** (line editors), before full-screen visual editors became standard.
- Vim is extremely **powerful** but has a reputation for being **cryptic** and **hard to learn**, especially for users coming from Windows-style GUI editors, because it relies on modal commands rather than menus and shortcuts.

### 1.2 Opening Vim

```
vim filename
```

This opens the file in **Normal mode**.

### 1.3 Modes

Vim is a _modal_ editor — the same keys do different things depending on which mode you're in.

|Mode|Purpose|How to enter|
|---|---|---|
|**Normal mode**|Default mode; navigate and run commands (no direct typing)|Press `Esc` from any other mode|
|**Insert mode**|Type and edit text directly|Press `i` from Normal mode|
|**Command-line mode**|Save, quit, search, run shell commands|Press `:` from Normal mode|
|**Visual mode**|Select and manipulate blocks of text|Press `v`, `V`, or `Ctrl+v` from Normal mode|

### 1.4 Command-Line Mode (Save/Quit)

Reached by pressing `Esc` (to return to Normal mode), then `:`

|Command|Action|
|---|---|
|`:w`|Save (write) the file|
|`:wq` or `:x`|Save and quit|
|`:q!`|Force quit without saving|

### 1.5 Running a Shell Command from Vim

From Command-line mode, prefix the command with `!`:

```
:!command
```

Example: `:!ls` runs `ls` in the shell without leaving Vim.

### 1.6 Visual Mode

Visual mode lets you select and manipulate blocks of text. There are three types:

|Type|Key|Behavior|
|---|---|---|
|**Character-wise**|`v`|Selects text character by character|
|**Line-wise**|`V` (Shift+v)|Selects entire lines at once|
|**Block-wise**|`Ctrl+v`|Selects a rectangular block of text across multiple lines and columns (useful for editing a "column" of text, e.g. adding the same prefix to several lines at once)|

---

## 2. Nano

### 2.1 Overview

Nano is a much **simpler, more beginner-friendly** terminal text editor than Vim. It is not modal — you type directly into the file, and common commands are shown at the bottom of the screen using `Ctrl` shortcuts.

### 2.2 Unsaved Changes Indicator

If a file has unsaved changes, Nano displays an **asterisk (`*`)** next to the filename in the title bar.

### 2.3 Key Shortcuts

|Shortcut|Action|
|---|---|
|`Ctrl + O`|**Save** the file (WriteOut)|
|`Ctrl + X`|**Exit** Nano|
|`Ctrl + T`|Execute an external command|

> **Note:** A common mix-up is using `Ctrl+S` to save — that shortcut doesn't apply in Nano. Saving is `Ctrl+O`, and exiting is `Ctrl+X`.

---

## 3. Quick Comparison

|Feature|Vim|Nano|
|---|---|---|
|Learning curve|Steep|Gentle|
|Editing style|Modal (Normal/Insert/Command/Visual)|Direct typing|
|Power/flexibility|Very high|Basic|
|Best for|Experienced users, heavy editing/scripting|Quick edits, beginners|