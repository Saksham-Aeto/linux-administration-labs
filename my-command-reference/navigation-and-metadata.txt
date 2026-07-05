# Navigation & Metadata Commands

---

## `type` — Identify Command Type

**What:** Shows if a command is a builtin, alias, or executable  
**Use:** `type [COMMAND]`

**Example:**
```bash
type ls     # Shows 'ls is aliased to...'
type cd     # Shows 'cd is a shell builtin'
```

---

## `which` — Locate Executable

**What:** Finds the absolute file path of an installed program  
**Use:** `which [PROGRAM]`

**Example:**
```bash
which python  # Outputs /usr/bin/python
```

---

## `man` — Manual Pages

**What:** Full documentation for executable programs  
**Use:** `man [COMMAND]`

**Options:**
- `/[search]` = Search for a word inside the manual
- `n` = Go to next search result
- `q` = Quit

**Example:**
```bash
man grep      # Opens the grep manual
```

---

## `help` — Builtin Help

**What:** Documentation for shell builtins (`cd`, `type`, `alias`)  
**Use:** `help [BUILTIN]`

**Options:**
- `-m` = Format output to look like a man page

**Example:**
```bash
help cd       # Shows options for changing directories
```

---

## `apropos` — Search Manuals by Keyword

**What:** Finds commands related to a specific search term  
**Use:** `apropos [KEYWORD]`

**Example:**
```bash
apropos partition  # Lists all commands dealing with partitions
```

---

## `whatis` — Quick Command Summary

**What:** Displays a one-line description of a command  
**Use:** `whatis [COMMAND]`

**Example:**
```bash
whatis ls   # Outputs "list directory contents"
```

---

## `info` — GNU Info Pages

**What:** Alternative to `man` with hyperlink-style navigation  
**Use:** `info [COMMAND]`

**Navigation:**
- `ENTER` = Follow link
- `u` = Go Up
- `p` = Go to Previous page
- `q` = Quit

**Example:**
```bash
info coreutils
```