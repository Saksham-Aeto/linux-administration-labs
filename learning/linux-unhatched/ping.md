# Ping

**Source:** Cisco NDG Linux Unhatched
**Date Started:** 2026-07-01
**Date Updated:** 2026-07-01

---

# Objective

Learn how to test network connectivity.

---

# Commands Learned

## `ping`

Used to verify connectivity between two computers.

Ping uses IP addresses to send data packets.

**Syntax:**

```bash
ping [OPTIONS] HOST
```

---

# Examples

```bash
ping google.com
```

```bash
ping 8.8.8.8
```

---

# Useful Options

## `-c`

Limits how many packets are sent.

Example:

```bash
ping -c 5 google.com
```

---

# Stopping Ping

Use:

```text
Ctrl + C
```

to stop sending packets.

---

# Failed Ping

You may see:

```text
Destination Host Unreachable
```

---

# Important Notes

A ping command may fail even if the remote machine is working.

Some administrators disable ping replies as a security measure.

Using:

```bash
ping hostname
```

checks both:

- DNS resolution.
- Network connectivity.

---

# Key Takeaways

- ping verifies connectivity.
- -c limits packet count.
- Ctrl+C stops ping.
- Failed ping does not always mean the machine is down.