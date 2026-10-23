# Episode 3: Help, Paths, and Basic File Operations

**Video:** [HELP!! (for when you suck at Linux) // EP3](https://www.youtube.com/watch?v=Y17KTiJLcyQ)
**Source evidence:** The public description presents help for command-line work. Its chapter markers cover `whoami`, `clear`, filesystem locations, `cat`, `cp`, `rm`, `adduser`, and `which`; the chapter list ranges across common directories and ends with a challenge.
**Practice level:** Read-only inspection first; file changes stay in a disposable home-directory folder.

## Learning objectives

- Find command documentation and identify how a command is resolved.
- Recognize common filesystem directories.
- Read and copy files safely, and understand why deletion needs care.

## Commands and behavior

| Command | Syntax and arguments | Effect |
| --- | --- | --- |
| `whoami` | `whoami` | Prints the effective user name. Inspect only. |
| `command -v` | `command -v NAME` | Shows how the shell resolves a command or function. Inspect only. |
| `man` | `man COMMAND` | Opens the installed manual page; press `q` to quit. |
| `cat` | `cat FILE...` | Writes file contents to the terminal. Inspect only; avoid dumping secrets to a shared terminal. |
| `cp` | `cp SOURCE DEST` | Copies a file; modifies the destination and may overwrite depending on options. |
| `rm` | `rm FILE` | Removes a directory entry. Destructive; there is usually no simple undo. |

The chapter list is direct evidence for these demonstrations. Use `--help` or the manual for exact option behavior because utilities and versions can differ.

## Safe practice in a Kali VM

```bash
whoami
command -v ls
man cp
mkdir -p "$HOME/linux-practice"
printf '%s\n' 'sample note' > "$HOME/linux-practice/original.txt"
cat "$HOME/linux-practice/original.txt"
cp -n "$HOME/linux-practice/original.txt" "$HOME/linux-practice/copy.txt"
ls -l "$HOME/linux-practice"
```

The `mkdir`, redirection, and `cp` examples change files under a dedicated practice directory. `-n` asks GNU `cp` not to overwrite an existing destination. Output contents and metadata depend on the local VM. Do not practise `rm` on valuable files.

## Common mistakes

- Running `cat` on binary files or sensitive logs and sending their contents to a terminal or transcript.
- Assuming `cp` always asks before replacing a destination.
- Using `rm` with wildcards or elevated privileges before checking what the pattern expands to.
- Treating `which` as universal; `command -v` also handles shell built-ins and functions.

## Security application

During triage, use read-only commands to identify your account, inspect file paths, and read relevant text. Preserve original evidence; copy into an approved working location before analysis.

## Revision questions

1. How can `man` and `--help` support safe command use?
2. What is the difference between `cat FILE` and `cp FILE DEST`?
3. Why is `rm` especially risky with a wildcard or `sudo`?
4. Which directories are commonly used for configuration, temporary data, and user home directories?

## References

- [Episode 3 video and chapters](https://www.youtube.com/watch?v=Y17KTiJLcyQ)
- [GNU Coreutils manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [GNU Bash manual](https://www.gnu.org/software/bash/manual/)
