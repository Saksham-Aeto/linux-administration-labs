# Chapter 6: Redirection

---

### **Redirection is the coolest feature of the command line. it's called I/O redirection.**
**It stands for Input and Output of commands to and from files, as well as connect multiple commands together into powerful command pipelines.**

## Standard Input, Output, and Error

Many of the programs that we have used so far produce output of some kind. This output often consists of two types:

- The program's results, that is, the data the program is designed to produce.
- Status and error messages that tell us how the program is getting along.

*ls* actually sends their results to a special file called **standard output (often expressed as stdout)** and their status messages to another file called **standard error (stderr).**

- I/O redirection allows us to change where output goes and where input comes from. Normally, output goes to the screen and input comes from the keyboard, but with I/O redirection, we can change that.

---

## Redirecting Standard Output

### > redirection operator

With the help of `>` redirection operator followed by the name of the file, we can redefine where standard output goes.

**NOTE** – With the use of `>`, the destination file is always rewritten from the beginning.

### Example

```bash
ls -l /usr/bin > ls-output.txt
```

### >> redirection operator

Using this will result in the output being appended to the file.

If the file does not exist, it is created just as though the `>` operator had been used.

**NOTE** – Repeating the same command with the `>>` operator increases the size of the file in proportion to how many times the command is repeated.

---

## Group Commands

It helps in executing a series of commands.

### Example of a normal command

```bash
command1; command2; command3

command1 > logfile.txt
command2 >> logfile.txt
command3 >> logfile.txt
```

Using group commands:

```bash
{ command1; command2; command3; } > logfile.txt
```

---

## Redirecting Standard Error

Redirecting standard error lacks the ease of a dedicated redirection operator.

To redirect standard error we must refer to its **file descriptor**.

A program can produce output on any of several numbered file streams.

The first three are:

- Standard Input
- Standard Output
- Standard Error

The shell references them as file descriptors:

- 0
- 1
- 2

### Example

```bash
ls -l /bin/usr 2> ls-error.txt
```

The file descriptor `2` is placed immediately before the redirection operator to perform the redirection of standard error to the file `ls-error.txt`.

---

## Redirecting Standard Output and Standard Error to One File

If we want to capture all the output of a command into a single file, there are two methods.

### Method 1

Redirect both standard output and standard error.

```bash
ls -l /bin/usr > ls-output.txt 2>&1
```

**Notice:** The order of the redirections is significant.

```
2>&1
```

### Method 2

Using the single notation:

```bash
ls -l /bin/usr &> ls-output.txt
```

---

## Disposing of Unwanted Output

```bash
ls -l /bin/usr 2> /dev/null
```

### What it does

`/dev/null` is a special file often referred to as the **bit bucket**.

It accepts input and discards it completely.

Useful for suppressing unwanted error messages.

---

## Redirecting Standard Input

### `cat` – Concatenate Files

The `cat` command reads one or more files and copies them to standard output.

```bash
cat [file...]
```

It can also be used to:

- Display files without paging.
- Join multiple files together.

Example:

```bash
cat movie.mpeg.0* > movie.mpeg
```

In the absence of filename arguments, `cat` copies standard input to standard output.

This can be used to create short text files.

Example:

```bash
cat > lazy_dog.txt

The quick brown fox jumps over the lazy dog.
```

---

## Pipelines

The capability of commands to read data from standard input and send it to standard output is utilized by a shell feature called **pipelines**.

Using the pipe operator `|`, the standard output of one command becomes the standard input of another.

### Format

```bash
command1 | command2
```

### Example

```bash
ls -l /usr/bin | less
```

This command is extremely handy.

---

## The Difference Between `>` and `|`

At first glance it may be difficult to understand the difference.

The `>` operator connects a command to a **file**.

The `|` operator connects the output of one command to the **input of another command**.

Examples:

```bash
command1 > file1

command1 | command2
```

Many beginners eventually try:

```bash
command1 > command2
```

Sometimes something really bad happens.

### Example

```bash
cd /usr/bin

ls > less
```

The shell overwrites the existing `less` executable with the output of `ls`, effectively destroying the `less` program.

### Lesson

The `>` operator silently creates or overwrites files.

Always be careful when redirecting output to filenames that already exist.
