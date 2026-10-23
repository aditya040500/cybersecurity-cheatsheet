# Episode 1: Getting Started with Linux

**Video:** [Linux for Hackers // EP 1 (FREE Linux course for beginners)](https://www.youtube.com/watch?v=VbEx7B_PTOE)
**Source evidence:** The public video description identifies Linux, the terminal, and chapters for `pwd`, `ls`, and `cd`.
**Practice level:** Safe inspection and navigation.

## Learning objectives

- Describe Linux as an operating system family built around the Linux kernel and distributions.
- Open a shell and distinguish the shell prompt from commands and their output.
- Find the current directory, list entries, and move between directories.

## Concepts

Linux distributions combine the kernel with system utilities, libraries, package-management tools, and applications. Kali is a Debian-based distribution oriented toward security work; its tools do not make activity authorized or safe by default. The terminal accepts commands through a shell. A command typically has a program name, options, and operands (values such as paths or hostnames).

| Command | Syntax | What it does |
| --- | --- | --- |
| `pwd` | `pwd` | Prints the shell's current working directory. |
| `ls` | `ls [OPTIONS] [PATH...]` | Lists directory entries. `-l` requests a long listing; `-a` includes dotfiles. |
| `cd` | `cd [PATH]` | Changes the current shell directory. `..` means parent; `~` normally means the current user's home. |

## Safe practice in a Kali VM

```bash
pwd
ls -la "$HOME"
cd "$HOME"
pwd
cd /etc
ls -la | head
```

These commands inspect locations and change only the current shell's working directory. Output depends on the VM user and installed files; no particular listing is expected. `head` limits the displayed listing to the first lines.

## Common mistakes

- Typing a path as if it were a command. Use `cd PATH` to navigate.
- Confusing an absolute path (starts with `/`) with a relative path (resolved from the current directory).
- Omitting quotes around paths with spaces.
- Assuming Kali is a separate kernel or that its toolset grants permission to test another system.

## Security application

Before inspecting a log, script, or configuration file, verify the current directory and target path. This reduces the chance of analyzing the wrong evidence or modifying an unintended file during later work.

## Revision questions

1. What does `pwd` report, and does it change system state?
2. How do `ls -a` and `ls -l` change a directory listing?
3. What is the difference between `/var/log` and `../var/log`?
4. Why does using Kali not by itself authorize a scan?

## References

- [Episode 1 video and chapters](https://www.youtube.com/watch?v=VbEx7B_PTOE)
- [GNU Coreutils manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [Bash manual](https://www.gnu.org/software/bash/manual/)
