
---

# `package-management.md`

```md
# Package Management

**Source:** Cisco NDG Linux Unhatched  
**Date Started:** 2026-07-02  
**Date Updated:** 2026-07-02

---

## Objective

Learn how software packages are installed, updated, searched, and removed in Linux.

---

## Important Concepts

Package management is the system used to:

- Install software
- Update software
- Search for software
- Remove software

Popular package management systems:

- Debian
- Red Hat

---

## Commands Learned

### Update Package List

```bash
sudo apt-get update
# Package Management
**Source:** Cisco NDG Linux Unhatched
**Date Started:** 2026-07-04
**Date Updated:** 2026-07-04

---

## Objective
Learn how software is installed, updated, searched for, and removed on a Debian-based Linux system (Ubuntu) using the APT package management system.

---

## Important Concepts
- Package management = system to install, update, query, or remove software from a filesystem
- Two most popular systems: Debian-based and Red Hat-based
- Ubuntu is a Debian derivative
- `dpkg` = low-level Debian package tool (tricky for beginners)
- `apt-get` = front-end program built on top of `dpkg`, easier to use
- A **front-end program** is one users directly see and interact with
- Debian repositories host 65,000+ packages
- Most package commands require `sudo` (administrative access)

---

## Commands Learned

### apt-get update
```bash
sudo apt-get update
```

Refreshes the local list of available packages from the repositories.

### apt-cache search

```bash
apt-cache search [keyword]
```

Example:

```bash
apt-cache search cow
```

### apt-get install

```bash
sudo apt-get install [package]
```

Example:

```bash
sudo apt-get install cowsay
```

### apt-get upgrade

```bash
sudo apt-get upgrade
```

### apt-get remove

```bash
sudo apt-get remove [package]
```

### apt-get purge

```bash
sudo apt-get purge [package]
```

Example:

```bash
sudo apt-get purge cowsay
```

---

## Key Takeaways

- Always run `apt-get update` before installing/upgrading.
- `remove` keeps config files, `purge` deletes everything.
- `apt-get` is the front-end; `dpkg` is the low-level engine.

---

## Practice Commands

```bash
sudo apt-get update
apt-cache search cowsay
sudo apt-get install cowsay
cowsay 'test message'
sudo apt-get purge cowsay
```

---

## Notes

- Enclose `cowsay` arguments in single quotes.
- Similar idea to `pip` and `npm`.

---

## Questions for Revision

- What's the difference between `dpkg` and `apt-get`?
- What happens if I run `apt-get upgrade` without `apt-get update`?
- When would I use `remove` instead of `purge`?