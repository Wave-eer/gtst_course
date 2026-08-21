# Advanced Linux Notes

## 1. User Management

### 1.1 Change a User's Password

```
sudo passwd username
```

- Adds a new password for users created with `useradd`
- Changes the password for users created with `adduser`

### 1.2 Change User/Group ID

```
sudo usermod -u newID username     # change user ID
sudo groupmod -g newID groupname   # change group ID
```

- The same or a different ID can be assigned to users and groups.

### 1.3 Delete a User

```
sudo userdel -r username
```

- `-r` force-deletes the user's home folder and files. Without it, deletion can fail or leave files behind.

### 1.4 Switch to Another User

```
su - username   # switch to the user
exit            # return to your normal user
```

**Why add multiple users?**

- Lets you separate tasks between accounts
- Reduces workload / risk on the main account

### 1.5 Create a Home Folder for a User

- Users created with `useradd` don't get a home directory automatically.

```
sudo mkhomedir_helper username
```

### 1.6 Change a User's Default Shell

```
sudo usermod username -s /bin/specifiedShell
```

- Note: the target shell must already be installed on the system.

---

## 2. Group Management

### 2.1 Create a New Group

```
sudo groupadd groupName
```

- Rarely needed — most users already have a group when created.

### 2.2 Add a User to a Group

```
sudo usermod -aG groupName userName
```

- `-aG` = append to group

### 2.3 Verify a User's Group Membership

```
groups userName
```

### 2.4 Remove a User from a Group

```
sudo gpasswd -d userName groupName
```

---

## 3. Sudoers File

- Controls which users are allowed to run `sudo` commands.
- Newly created users are **not** automatically added to the sudoers file, so they can't use `sudo` until granted access.
- Edit the file with:

```
sudo visudo
```

- Only works when run as/from the original ("normal") user account.

---

## 4. Linux File Permissions

### 4.1 Viewing Ownership & Permissions

```
ls -l
```

Output shows 5 main parts: **Permissions, Owner, Date, Size, Filename**

### 4.2 Ownership

- Two kinds of owner: **User** and **Group**
- Change ownership:

```
sudo chown user:group filename
```

### 4.3 Permission Types

|Permission|Symbol|Meaning|
|---|---|---|
|Read|r|View file contents / list folder contents|
|Write|w|Add or remove content from a file/folder|
|Execute|x|Run a file (e.g. a `.java` or `.js` script)|

- Full permission string = 9 characters: **user (3) + group (3) + other (3)**
- First character indicates type: `d` = directory, `-` = file

### 4.4 Permission Targets

|Target|Symbol|Meaning|
|---|---|---|
|User|u|Owner's permissions|
|Group|g|Group's permissions|
|Other|o|Everyone else's permissions|
|All|a|User + Group + Other|

### 4.5 Changing Permissions — `chmod`

Numeric values: **Read = 4, Write = 2, Execute = 1**

**Symbolic syntax:**

```
chmod a+x filename                     # add execute for everyone
chmod u+x filename                     # add execute for the user only
chmod -x filename                      # remove execute for everyone
chmod a+rwx,u-rw,g-x,o-xw filename     # grant rwx to all, then selectively remove
```

**Numeric syntax:**

```
chmod 621 filename   # 6=user, 2=group, 1=other
```

### 4.6 Special File Permissions

|Type|Symbol|Adds|Notes|
|---|---|---|---|
|SUID (Set User ID)|s|4000|Runs the file as the file's owner, regardless of who executes it|
|SGID (Set Group ID)|s|2000|Runs the file with the group's permissions|
|Sticky bit|t|1000|Restricts deletion; weaker than SUID/SGID — read/execute-oriented only|

- These act like execute permission, but the process runs with the permissions of whoever _set_ the bit — no `sudo` required at runtime.

---

## 5. Package Management

### 5.1 Overview

- Software is installed via a **package manager** (e.g. `apt`, `pacman`, `pkg`).
- On Debian-based distros, the main tools are **APT** and **dpkg**.
- Installing a package also installs its **dependencies** (supporting files/modules the software needs) and its **metadata** (extra info about the package).
- A **repository** is the server hosting the packages; internet access is needed to reach it.

### 5.2 APT (Advanced Package Tool)

- Free, user-friendly interface to an online repository.
- Installation requires internet; removal can be done offline.
- Formerly known as `apt-get`.

```
sudo apt update            # check for available updates
sudo apt search software   # check if a package exists in the repo
sudo apt install software  # install a package
sudo apt remove software   # remove the package only
sudo apt upgrade           # update installed packages automatically
sudo apt purge software    # remove package + dependencies + metadata
```

#### Common APT/Repository Errors

|Error|Cause|Fix|
|---|---|---|
|`Could not get lock - /var/lib/apt/lists/lock`|Two `apt` processes running at once|Close the other process, or restart the PC|
|`Could not open lock - /var/lib/dpkg/lock-frontend`|Forgot to run `apt` with `sudo`|Re-run the command with `sudo`|
|`Unable to locate package`|Package name misspelled|Check spelling and retry|
|`Repository "kali repo" doesn't have a release file`|Repository config problem (broken/outdated link)|Check `/etc/apt/sources.list`, or run `sudo apt edit-sources`|

- Don't close APT while an installation is in progress.

### 5.3 dpkg (Debian Package Manager)

- Offline package manager — used for installing local `.deb` files.
- Debian packages use the `.deb` extension.

```
sudo dpkg -i packageName   # install
sudo dpkg -r packageName   # remove (package only)
sudo dpkg -p packageName   # purge (package + dependencies + metadata)
```

### 5.4 Flatpak

- Universal packaging/distribution system that works across **any** Linux distro.
- Simplifies developing, distributing, and installing apps across distros.

```
sudo apt install flatpak            # install flatpak itself
flatpak install flathub appName     # install an application
flatpak run appName                 # run an application
flatpak search appName              # search for an application
flatpak uninstall appName           # uninstall an application
flatpak update                      # update all flatpak apps
flatpak list                        # list installed flatpak apps
flatpak --version                   # check flatpak is working
```