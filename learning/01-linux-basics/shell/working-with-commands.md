# Chapter 5: Working With Commands

---

## `help`

### What it does

Provides documentation specifically for shell builtins (like `cd` or `type`), which `man` sometimes struggles with or groups together confusingly.

### Syntax

```bash
help [builtin_command]
```

### Example

```bash
help cd
```

### My Review & Mistakes

I tried using `man cd` and got a massive page covering bash itself instead of just the `cd` command. I learned that for shell builtins, `help` is much faster and gives me exactly what I need without the extra noise. Adding `-m` (`help -m cd`) formats it like a man page if I want it easier to read.

---

## `apropos` and `whatis`

### What they do

- `apropos`: Searches the manual pages for a keyword. Great for when I know what I want to do, but forgot the command name.
- `whatis`: Gives a fast, one-line summary of what a command does.

### Syntax

```bash
apropos [keyword]
whatis [command]
```

### Examples

```bash
apropos partition
whatis ls
```

### My Review & Mistakes

`apropos` is basically my command-line search engine. If I forget how to copy a file, I can just type `apropos copy`. `whatis` is perfect for a quick memory jog when I don't want to read a full `man` page just to remember what `grep` does.

---

## `info`

### What it does

The GNU Project's alternative to `man` pages. It is formatted more like a website with hyperlinks (nodes) you can navigate through using the keyboard.

### Syntax

```bash
info [command]
```

### Example

```bash
info coreutils
```

### My Review & Mistakes

I found `info` a bit clunky to navigate at first. Hitting `ENTER` on a link with an asterisk (`*`) moves you forward, and pressing `u` (Up) or `p` (Previous) moves you back. Press `q` to quit. I will stick to `man` mostly, but `info` is good to know if `man` isn't detailed enough.

---

## `alias`

### What it does

Creates a custom shortcut for a command. You can combine multiple commands or add default options to commands you use all the time.

### Syntax

```bash
alias name='string_of_commands'
unalias name
```

### Examples

```bash
alias update='sudo apt update; sudo apt upgrade'
alias foo='cd /usr; ls; cd -'
```

### My Review & Mistakes

I created an alias, tested it, and it worked perfectly. But when I closed the terminal and reopened it, the alias was gone! I learned that aliases created in the terminal are temporary. To make them permanent, they need to be added to my environment files later on (Chapter 11).