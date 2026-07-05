# Shell Scripting Commands

---

## `alias` / `unalias` — Custom Command Shortcuts

**What:** Creates or removes a custom shortcut for terminal commands

**Use:**
```bash
alias [NAME]='[COMMAND]'
unalias [NAME]
```

**Note:** Aliases created in the terminal vanish when the session ends.

**Examples:**
```bash
alias                    # View all currently active aliases
alias ll='ls -l --color=auto'  # Creates 'll' shortcut
unalias ll               # Removes the shortcut
```