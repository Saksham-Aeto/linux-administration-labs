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
Module 3: Directory Listing & Investigation (ls)

**The ls Command (List):
**
**What it does:** Displays the contents (files and folders) of a directory.

**Operational Reality:** It is the flashlight of the CLI. Once you cd into a directory, you use ls to see what is actually inside it.

**Execution**: Typing ls by itself lists the contents of your current directory. Typing ls /var/log lists the contents of the /var/log directory without moving you there.

**Essential ls Options (Flags):**

**ls -l (Long Format): **The most critical option. It prints a detailed vertical list. It reveals the ID Card of every file, showing its permissions, owner, file size, and the exact timestamp it was last modified.

**ls -lt (Time Sort):** Sorts the output chronologically. The most recently modified files are pushed to the very top. Crucial for sysadmins looking for a log file that just updated after a crash.

**ls -lS (Size Sort):** Sorts the output by file size. The largest files are at the top. Crucial for sysadmins trying to find out what is eating up all the hard drive space.

**ls -r (Reverse): **Reverses the sorting order. For example, ls -lSr puts the smallest files at the top, and ls -ltr puts the oldest files at the top.

How to Read -l Output (File Types):

When you run ls -l, look at the very first character on the far left of the output.

(Dash): Indicates a regular, standard file (text file, image, binary).

d (Directory): Indicates it is a folder containing other files.
