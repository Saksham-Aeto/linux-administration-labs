all the notes go here.
# Linux Administration & Infrastructure Labs

A public log of my hands-on experience with Linux systems management, CLI administration, and directory structures.

## Lab 1: Filesystem Navigation & Absolute vs. Relative Paths

### Core Commands Mastered:
* `pwd` - Print Working Directory. Identifies the exact absolute location within the system.
* `ls` - Lists directory contents.
  * `ls -l` - Long listing format (displays file permissions, ownership, and size).
  * `ls -r` - Reverses the sorting order of the output.
  * `ls -rl` - Combines flags to show long listing format in reverse order.
* `cd` - Change Directory.
  * `cd /` - Navigates straight to the **Root Directory** (the absolute base of the OS filesystem).
  * `cd ..` - Moves exactly one level up to the parent directory.

### Key Technical Takeaway:
* **Absolute Paths:** Always begin with a forward slash `/`, representing a path starting from the Root directory (e.g., `cd /var/log`).
* **Relative Paths:** Do not begin with a slash; they navigate relative to the current directory location (e.g., `cd Documents/School/Cs`).
### Lab 2: Directory Investigation & Metadata Analysis (`ls`)

**Core Commands Mastered:**

* **`ls`** - Lists directory contents. Acts as the primary visual investigation tool for system administrators. 
* **`ls /var/log`** - Executes the list command against a distant absolute path without requiring a directory change (`cd`).
* **`ls -l`** - Long listing format. Reveals critical file metadata including permissions, ownership, exact file size, and modification timestamps.
* **`ls -lt`** - Time Sort. Organizes output chronologically, pushing the most recently modified files to the top (critical for crash log analysis).
* **`ls -lS`** - Size Sort. Organizes output by file size, placing the largest files at the top (used for storage troubleshooting and capacity planning).
* **`ls -r`** - Reverses the default sorting order. Can be chained with other flags (e.g., `ls -lSr` puts the smallest files at the top, and `ls -ltr` puts the oldest files at the top).
---

## Date: 2026-06-16 | Lab 3: Administrative Access & File Permissions

### 1. Privilege Escalation (`su` vs. `sudo`)
* **`su -` (Substitute User):** * Switches your entire terminal session to the `root` user (or another specified user).
  * Creates a completely new shell environment (the `-` ensures it loads the root's specific environment variables).
  * **Risk:** High. You remain logged in as root (`#` prompt) until you explicitly type `exit`.
* **`sudo` (Superuser Do):**
  * Executes a *single command* with root privileges without leaving your current user shell.
  * **Risk:** Low. Once the single command finishes, you are instantly back to your safe, regular user privileges (`$` prompt). This is the industry standard for safe system administration.

### 2. Changing File Permissions (`chmod`)
* **Core Concept:** Only the file's owner or the root user can change permissions. `chmod` stands for "change mode of access."
* **The Symbolic Method Syntax:** `chmod [<SET><ACTION><PERMISSIONS>] filename`
  * **Sets:** Who gets the permission?
    * `u` = User (Owner)
    * `g` = Group
    * `o` = Others
    * `a` = All
  * **Actions:** What are we doing?
    * `+` = Add permission
    * `-` = Remove permission
    * `=` = Set exact permission (overwriting previous)
  * **Permissions:** What access is granted?
    * `r` = Read
    * `w` = Write
    * `x` = Execute (Required to run a script or program)
---

## Date: 2026-06-16 | Lab: The Linux Filesystem Hierarchy

### Core Directories (The "Filing Cabinet")
* **`/` (Root):** The absolute base of the filesystem. Everything branches from here.
* **`/etc` (Configuration):** System-wide configuration files (e.g., `/etc/passwd` for user info). If you are changing a server setting, you are editing a file in here.
* **`/var` (Variable Data):** Files that change frequently. Most importantly, **`/var/log`**, which holds the system error and activity logs. 
* **`/home`:** Personal directories for regular users. 
* **`/bin` & `/sbin` (Binaries):** Where the actual executable programs live. When you type commands like `ls` or `pwd`, the system is running a program located in `/bin`.
* **`/dev` (Devices):** Proves the rule that "Everything is a file." Hardware devices (hard drives, webcams) are represented as files here.
* **`/tmp` (Temporary):** The system's scratchpad. Often completely wiped on a reboot. 

### Symbolic Links (Symlinks)
* Denoted by an `l` in the `ls -l` output (e.g., `lrwxrwxrwx`).
* Acts as a shortcut pointing to another file or directory (`fileA -> fileB`).

**Key Technical Takeaway:**

* **File Type Indicators:** When analyzing a long format (`-l`) output, the absolute first character dictates the system object type. A dash (`-`) indicates a standard file (text, image, or binary), while a `d` indicates a directory folder.
* **Targeted Execution:** You do not need to stand inside a room to see what is in it. Executing commands against specific paths saves time and prevents unnecessary navigation operations.
Lab Report: Linux Access Control & Identity Management
Date: 2026-06-20
Module: User Permissions and Ownership

1. File Permission Modes (chmod)
The Linux permission system is a bitmask applied to an Inode. When you interact with chmod, you are not just toggling switches; you are modifying the metadata bits of the file system.

The Bitwise Logic Table
Permission	Symbolic	Octal Value	System Capability
Read	r	4	Allows viewing file content/listing directory
Write	w	2	Allows modifying, deleting, or renaming
Execute	x	1	Allows running binaries or entering directory

The chmod Syntax Architecture
chmod [SET][ACTION][PERMISSION] [FILE]

The SET (The Target): Who are we changing? u (owner), g (group), o (others), a (all).

The ACTION (The Operator): How do we change it? + (add), - (remove), = (set exact).

The PERMISSION (The Access): What are we changing? r, w, or x.

Profound Takeaway: The x Bit
Files: The x bit allows the OS kernel to load the file into memory as a process. Without this, the shell will reject the execution request with Permission denied, regardless of your ownership status.

Directories: The x bit is the "key" to the room. It allows you to enter a directory (using cd). Without x, you cannot access any file inside that directory, even if you have read access.

2. File Ownership (chown)
Ownership defines the Security Principal. In Linux, every file is owned by a UID (User ID) and a GID (Group ID). The name root or sysadmin is merely an alias for these numerical IDs.

The Hierarchy of Authority
The Owner: Can change permissions and modify the file.

The root (UID 0): The absolute sovereign. Can override any permission bit on the system.

The Others: Bound strictly by the permission bits defined for them.

Deep Dive: Ownership Constraints
Why can't I chown my own files to someone else?
This is a hard-coded security feature of the Linux kernel to prevent "quota theft" and "permission escalation." If you could give your files to another user, you could trick them into executing malicious code while they assume the blame for the file's content.

The sudo ./file paradox:
If you chown a file to root, you lose the ability to edit it as a normal user. Executing it with sudo works because sudo elevates your process identity to UID 0 (root) for that execution cycle.

Engineering Reflection
The "Permission Denied" diagnostic: * Is it a Permission issue? (Check ls -l and adjust chmod).

Is it an Ownership issue? (Check if the file belongs to root or another user).

Is it a Path issue? (Remember: ./ is required to execute files in your current directory).
