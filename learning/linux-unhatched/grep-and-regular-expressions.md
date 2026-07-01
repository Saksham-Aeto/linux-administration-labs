# Grep and Regular Expressions

**Source:** Cisco NDG Linux Unhatched
**Date Started:** 2026-07-01
**Date Updated:** 2026-07-01

---

# Objective

Learn how to filter text using grep and understand regular expressions.

---

# Commands Learned

## `grep`

The grep command is a text filter. It filters file lines or inputs and only checks for the pattern you set.

**Syntax:**

```bash
grep [OPTIONS] PATTERN [FILE]
```

It can also be used to filter out information about a specific user.

---

# Literal Characters

Just type what you want to find.

Use single quotes to stop the shell from interpreting special characters.

Example:

```bash
grep 'root' /etc/passwd
```

---

# Anchor Characters

## `^`

Start of line.

```bash
grep '^root' /etc/passwd
```

Only shows lines that start with "root".

---

## `$`

End of line.

```bash
grep 'r$' alpha-first.txt
```

Only shows lines that end with "r".

---

# Important

- `^` must be first in the pattern.
- `$` must be last in the pattern.

---

# Dot `.`

Matches exactly one character.

Example:

```bash
grep 'c.t' file.txt
```

Matches:

```text
cat
cut
cot
```

---

# Star `*`

The previous character can appear zero or more times.

Example:

```bash
grep 'ca*t' file.txt
```

Matches:

```text
ct
cat
caat
caaat
```

---

# Basic Regular Expressions

| Character | Meaning |
|-----------|----------|
| . | Any one single character |
| [ ] | Any one specified character |
| [^ ] | Not the specified character |
| * | Zero or more of previous character |
| ^ | Beginning of line |
| $ | End of line |

---

# Extended Regular Expressions

Use with:

```bash
grep -E
```

or

```bash
egrep
```

| Character | Meaning |
|-----------|----------|
| + | One or more |
| ? | Optional |
| { } | Minimum, maximum or exact matches |
| \| | Logical OR |
| ( ) | Groups |

---

# Additional Regex Symbols

| Symbol | Meaning |
|--------|----------|
| {n} | Exactly n times |
| {n,} | n or more times |
| {n,m} | Between n and m times |
| \ | Escape special characters |
| \b | Word boundary |
| \d | Digit |
| \w | Word character |

---

# Key Takeaways

- grep filters text.
- Regular expressions make searching powerful.
- Basic and extended regex have different features.
- Use single quotes when working with patterns.