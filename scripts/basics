# Shell Scripts

**Source:** The Linux Command Line (William Shotts)  
**Chapter:** 5 (Introduction to Shell Scripts)  
**Date Started:** 2026-07-07  
**Date Updated:** 2026-07-07

---

## Objective

Learn what a shell script is, how to create one, make it executable, and run it from the terminal.

---

## What is a Shell Script?

A shell script is a plain text file containing Linux commands that are executed sequentially by the shell.

Instead of typing multiple commands manually, they can be written once inside a script and executed whenever needed.

---

## Important Concepts

- A shell script is simply a text file.
- Commands execute from top to bottom.
- Scripts automate repetitive tasks.
- Bash scripts usually begin with a **shebang**.
- A script must have execute permission before it can be run directly.

---

## Commands Learned

### Create a Script

```bash
touch hello.sh
```

Creates an empty shell script.

---

### Edit a Script

```bash
nano hello.sh
```

Opens the script in the Nano text editor.

---

### Make a Script Executable

```bash
chmod +x hello.sh
```

Adds execute permission so the script can be run directly.

---

### Run the Script

```bash
./hello.sh
```

Executes the script located in the current directory.

---

## First Script

```bash
#!/bin/bash

echo "Hello Aeto!"

pwd

ls
```

### Explanation

| Line | Purpose |
|------|----------|
| `#!/bin/bash` | Runs the script using the Bash shell. |
| `echo` | Prints text to the terminal. |
| `pwd` | Displays the current working directory. |
| `ls` | Lists files in the current directory. |

---

## Debugging Experience

While running the first script, the following error occurred:

```text
./hello.sh: line 2: exho: command not found
```

Cause:

- `echo` was mistakenly typed as `exho`.

Fix:

- Corrected the spelling from `exho` to `echo`.

Lesson Learned:

- Read terminal error messages carefully.
- Bash reports the line number where an error occurs.
- By default, Bash continues executing the remaining commands even if one command fails.

---

## Key Takeaways

- Shell scripts automate Linux commands.
- Every command inside a script is executed in order.
- `chmod +x` makes a script executable.
- `./script-name` runs a script from the current directory.
- Reading error messages is an important debugging skill.

---

## Practice Commands

```bash
touch hello.sh
nano hello.sh
chmod +x hello.sh
./hello.sh
```

---

## Notes

- A shell script is simply a sequence of Linux commands.
- Scripts become more powerful as Bash features such as variables, loops, and functions are introduced.
- Understanding simple scripts is the foundation for Linux automation.

---

## Questions for Revision

- What is a shell script?
- Why is `#!/bin/bash` used?
- Why do we use `chmod +x`?
- Why do we run scripts using `./script.sh`?
- How do you identify the line causing an error in a Bash script?
