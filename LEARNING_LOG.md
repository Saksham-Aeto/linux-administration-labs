
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
Here's the refined version ready to paste:

---

## Date: 2026-06-20 | Lab: Access Control & Identity Management

### 1. File Permission Modes (chmod)

The Linux permission system modifies the metadata bits of a file stored in its Inode. chmod does not toggle switches — it rewrites access rules at the filesystem level.

| Permission | Symbolic | Octal Value | Capability |
|------------|----------|-------------|------------|
| Read | r | 4 | View file contents or list directory |
| Write | w | 2 | Modify, delete, or rename |
| Execute | x | 1 | Run binaries or enter a directory |

**Syntax:** chmod [SET][ACTION][PERMISSION] [FILE]

- SET — who: u (owner), g (group), o (others), a (all)
- ACTION — how: + (add), - (remove), = (set exact)
- PERMISSION — what: r, w, or x

**Profound Takeaway — The x Bit:**

On a file — x allows the kernel to load it into memory as a process. Without it, execution is rejected with Permission denied regardless of ownership.

On a directory — x is the key to the room. Without it you cannot cd into the directory even if you can see it exists.

---

### 2. File Ownership (chown)

Every file is owned by a UID and GID. Names like root or sysadmin are just aliases for numerical IDs.

**Hierarchy of Authority:**
- Owner — can change permissions and modify the file
- root (UID 0) — absolute authority, overrides any permission
- Others — bound strictly by permission bits assigned to them

**Why can't you chown your files to someone else?**
Hard coded kernel security. It prevents quota theft and permission escalation — you could otherwise trick another user into executing malicious code under their identity.

**The sudo ./file paradox:**
Chowning a file to root means you lose edit access as a normal user. Running it with sudo works because sudo elevates your process to UID 0 for that execution cycle only.

---

### Engineering Reflection — Permission Denied Diagnostic

1. Permission issue? — check ls -l and adjust with chmod
2. Ownership issue? — check if file belongs to root or another user
3. Path issue? — remember ./ is required to execute files in your current directory

---

## Date: 2026-06-21 | Lab: File Viewing & File Operations

### Core Commands Mastered:

**cat** - Concatenate. Used to quickly view the full contents of small files.
Syntax: cat [OPTIONS] [FILE]

**head** - Views only the top portion of a file.
**tail** - Views only the bottom portion of a file.
Both use* -n *to specify exact number of lines to view.
Syntax: head -n number_of_lines filename

**cp** - Copy. Creates a copy of a file from a source to a destination.
Syntax: cp [OPTIONS] SOURCE DESTINATION

### Key Technical Takeaway:

~ (tilde) is a shortcut that always points to your home directory (/home/yourusername), not the root directory (/). So cd ~/Documents navigates to your personal Documents folder, not a system level one.

### Lab Note:

cp command practiced in theory. Requires a real Linux terminal (like the Unhatched VM) to execute — GitHub browser editor is for file management only, not running commands.

---
## Day 1 — Linux Unhatched: File Management (mv, rm)

### Moving Files — `mv`

The `mv` command moves a file from one location in the file system to another.

**Syntax:**
```bash
mv SOURCE DESTINATION
```

**Example:**
```bash
mv people.csv Work
```

**Key points:**
- Two things are required for this command to work:
  1. **Source** — where the file is to be moved from
  2. **Destination** — where the file is moved to
- If the file is moved without specifying a new name, it retains its original name.
- `mv` can move multiple files at once, as long as the final argument is the destination.

> **Consider this:** Permissions can affect file management commands like `mv`. Moving a file requires **write** and **execute** permissions on both the origin and destination directories.

---

### Removing Files — `rm`

The `rm` command deletes files and directories.

**Syntax:**
```bash
rm [OPTIONS] [FILES]
```

**Key points:**
- Deleted files/directories do **not** go to a "trash can" the way they do on a desktop — they are **permanently deleted** and cannot be recovered.

> **Consider this:** Permissions can affect file management commands like `rm`. To delete a file within a directory, a user must have **write** and **execute** permission on that directory. Regular users typically only have this level of permission in their home directory and its subdirectories.
