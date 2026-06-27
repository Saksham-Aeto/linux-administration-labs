# Navigation

**Source:** Cisco NDG Linux Unhatched
**Date Started:** 2026-06-18
**Date Updated:** 2026-06-27

---

# Objective

Learn how to move around the Linux filesystem and discover the current location.

---

# Commands Learned

## `pwd`

**Purpose:** Used to discover your current location in the filesystem.

**Syntax:**

```bash
pwd [OPTIONS]
```

---

## `cd`

**Purpose:** This command is used to change directories (move around).

**Syntax:**

```bash
cd [OPTIONS] [PATH]
```

### Common Usage

```bash
cd /
```

Means to be in the root directory.

```bash
cd ..
```

Used to take a step toward the parent directory.

---

# Core Concepts

## Absolute Paths

An absolute path allows you to specify the exact location of a directory. It always starts at the root directory, therefore it always begins with the `/` character.

**Example:**

```text
/var/log
```

---

## Relative Paths

A relative path gives directions to a file relative to your current location in the filesystem.

Relative paths do not start with the `/` character, they start with the name of a directory.

**Example:**

```text
Documents/School
```

---

# Practical Exercises

* [x] Navigate to `/var/log`
* [x] Return to your home directory
* [x] Create and enter a new directory
* [x] Use both absolute and relative paths

---

# Reflection

## Things that confused me
at first i had problems while navigating as i have to type the whole absolute path and a single misclick and i have to try again,
but i soon got used to it. 
**in conclusion -** you must have a whole overview of where things are it makes things way easier.

*

## Things I understand now
** why was cd .. needed ? that was what i though at first as when you have cd to move around why this ?**
* Ans: **convinence**
*
