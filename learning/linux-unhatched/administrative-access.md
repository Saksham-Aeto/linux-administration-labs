# Administrative Access

**Source:** Cisco NDG Linux Unhatched
**Date Started:** 2026-06-19
**Date Updated:** 2026-06-27

---

# Objective

Learn how Linux temporarily grants administrative privileges.

---

# Commands Learned

## `su`

**Syntax:**

```bash
su [OPTIONS] USERNAME
```

The `su` command allows you to temporarily act as a different user. It does this by creating a new shell.

The shell is simply a text input console that lets you type commands.

By default, if a user account is not specified, the `su` command will open a new shell as the root user, which provides administrative privileges.

After executing the `su` command, a password is required.

---

## `sudo`

**Syntax:**

```bash
sudo [OPTIONS] COMMAND
```

The `sudo` command allows a user to execute a command as another user without creating a new shell.

Instead, to execute a command with administrative privileges, use it as an argument to the `sudo` command.

Like the `su` command, the `sudo` command assumes by default the root user account should be used to execute commands.

---

# Consider This

The `sudo` command can be used to switch to other user accounts as well.

To specify a different user account use the `-u` option.

Example:

```bash
sudo -u username command
```

---

# Key Differences

| su                             | sudo                               |
| ------------------------------ | ---------------------------------- |
| Creates a new shell            | Executes a single command          |
| Requires switching users       | Temporary privilege elevation      |
| Stays in root shell until exit | Returns to normal user immediately |

---

# Key Takeaways

* `su` creates a new shell.
* `sudo` executes a command with elevated privileges.
* `sudo` is generally safer because it limits administrative access.
