# Text Editor (vi / vim)
**Source:** Cisco NDG Linux Unhatched
**Date Started:** 2026-07-04
**Date Updated:** 2026-07-04

---

## Objective

Learn the fundamentals of the `vi` text editor.

---

## Important Concepts

- `vi` is available on every Linux distribution.
- Most systems actually run `vim`.
- Three modes:
  - Command mode
  - Insert mode
  - Ex mode

---

## Commands Learned

### Open a file

```bash
vi filename.txt
```

### Movement

| Key | Result |
|---|---|
| h / j / k / l | left / down / up / right |
| w | one word forward |
| b | one word back |
| ^ | beginning of line |
| $ | end of line |
| 5G | line 5 |
| gg | first line |
| G | last line |
| Ctrl+G | show line number |

### Editing

| Action | Meaning |
|---|---|
| dd | delete line |
| 3dd | delete 3 lines |
| dw | delete word |
| cc | change line |
| cw | change word |
| yy | copy line |
| 3yy | copy 3 lines |
| p | paste after |
| P | paste before |

### Insert Mode

| Key | Meaning |
|---|---|
| i | insert before |
| a | insert after |
| I | beginning of line |
| A | end of line |
| o | new line below |
| O | new line above |

### Search

```bash
/pattern
?pattern
```

### Ex Commands

| Command | Purpose |
|---|---|
| :w | save |
| :w filename | save as |
| :w! | force save |
| :q | quit |
| :q! | quit without saving |
| :1 | line 1 |
| :e filename | open file |
| ZZ | save and quit |

---

## Key Takeaways

- Press Esc to return to command mode.
- `d` = cut.
- `y` = copy.
- `p` = paste.

---

## Practice Commands

```bash
vi newfile.txt
i
:w
dd
yy
p
/searchterm
:q!
```

---

## Notes

- Everything is keyboard-driven.
- Easy mistake: forgetting Esc.

---

## Questions for Revision

- Difference between vi and vim?
- Why does `:q` fail sometimes?
- What is visual mode?