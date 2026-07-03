# Redirection
**Source:** Cisco NDG Linux Unhatched
**Date Started:** 2026-07-04
**Date Updated:** 2026-07-04

---

## Objective

Understand I/O (input/output) redirection in Linux.

---

## Important Concepts

- I/O redirection sends information from the command line to files.
- Three file descriptors:
  - STDIN
  - STDOUT
  - STDERR
- `>` overwrites.
- `>>` appends.

---

## Commands Learned

### Redirect (overwrite)

```bash
[COMMAND] > [FILE]
```

Example:

```bash
cat food.txt > newfile1.txt
```

### echo

```bash
echo "text"
```

Example:

```bash
echo "I like food." > newfile1.txt
```

### Redirect (append)

```bash
[COMMAND] >> [FILE]
```

Example:

```bash
echo "This food is good." >> newfile1.txt
```

---

## Key Takeaways

- `>` = overwrite.
- `>>` = append.
- Redirected output goes into a file, not the terminal.

---

## Practice Commands

```bash
cd ~/Documents
cat food.txt
cat food.txt > newfile1.txt
cat newfile1.txt
echo "I like food." > newfile1.txt
echo "This food is good." >> newfile1.txt
cat newfile1.txt
```

---

## Notes

- Accidentally using `>` can wipe out a file.
- `2>` for STDERR is a later topic.

---

## Questions for Revision

- How do you redirect STDERR?
- Can STDOUT and STDERR go to the same file?
- Does `>` create a file if it doesn't exist?