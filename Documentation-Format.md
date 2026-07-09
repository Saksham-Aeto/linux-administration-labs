# Chapter X: [Topic Name]

**Source:** The Linux Command Line – William Shotts
**Chapter:** X
**Topic:** [Main Topic]
**Date Started:** YYYY-MM-DD
**Date Completed:** YYYY-MM-DD

---

# Objective

What is this chapter trying to teach?

Example:

Understand Linux I/O redirection, pipelines, and how commands communicate through standard streams.

---

# Concepts Covered

- Standard Input (stdin)
- Standard Output (stdout)
- Standard Error (stderr)
- Output Redirection
- Pipelines
- tee
- /dev/null

---

# Concept Notes

## Standard Output (stdout)

### Definition

Normal output produced by a command.

### Default Destination

Terminal

### File Descriptor

1

### Example

```bash
ls
```

### Personal Understanding

Normal output is sent to the terminal unless redirected.

---

## Standard Error (stderr)

...

---

# Commands Learned

## `>`

### Purpose

Redirect stdout to a file.

### Syntax

```bash
command > file
```

### Example

```bash
ls > output.txt
```

### Notes

Overwrites the file if it already exists.

---

## `>>`

...

---

# Commands Practiced

```bash
ls > output.txt

echo "Hello" >> output.txt

cat output.txt

ls | less

history | less

ls | tee output.txt
```

---

# Important Observations

- `>` overwrites files.
- `>>` appends data.
- `|` sends output to another command.
- `tee` writes to both screen and file.
- `/dev/null` discards unwanted output.

---

# Common Mistakes

Example:

Using

```bash
ls > less
```

can overwrite an existing executable if you're in the wrong directory.

---

# Debugging Notes

Problems encountered while practicing.

How they were solved.

---

# Real World Uses

Example:

- Redirect logs to a file.
- Save command output.
- Build pipelines.
- Suppress unnecessary errors.

---

# Personal Reflection

Today I learned...

The most confusing concept was...

What finally made it click...

---

# Revision Summary

- stdout = FD 1
- stderr = FD 2
- stdin = FD 0
- `>` overwrite
- `>>` append
- `|` pipeline
