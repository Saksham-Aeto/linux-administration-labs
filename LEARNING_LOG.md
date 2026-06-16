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

**Key Technical Takeaway:**

* **File Type Indicators:** When analyzing a long format (`-l`) output, the absolute first character dictates the system object type. A dash (`-`) indicates a standard file (text, image, or binary), while a `d` indicates a directory folder.
* **Targeted Execution:** You do not need to stand inside a room to see what is in it. Executing commands against specific paths saves time and prevents unnecessary navigation operations.
