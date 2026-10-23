# Episode 10: File Operations and Failure Modes

**Video:** [i KILLED my Linux computer!! (to teach you something)](https://www.youtube.com/watch?v=ugt3PBeqHIo)
**Source evidence:** The public description says the episode demonstrates breaking a Linux system and creating a very large number of directories. Indexed chapter markers name `echo`, `mkdir`, `mv`, and `cp`; the video is part of the playlist. These examples are deliberately treated as hazardous demonstrations, not recommended practice.
**Practice level:** Safe file operations only, inside a disposable VM snapshot and a dedicated temporary directory.

## Learning objectives

- Understand how simple file and directory operations can have a large effect when paths, loops, or volume are uncontrolled.
- Distinguish creating, copying, moving, overwriting, and deleting data.
- Practise only bounded operations in a directory created for the exercise.

## Commands identified by the public chapters

| Syntax | Purpose | Risk |
| --- | --- | --- |
| `echo TEXT > FILE` | Writes text through shell redirection. `>` creates or truncates the destination. | Overwrites an existing file. |
| `mkdir DIR` | Creates one directory. | Low if the path is deliberate; repeated creation can consume storage/inodes. |
| `mv SOURCE DEST` | Moves or renames a path. | May replace a destination or make files harder to locate. |
| `cp SOURCE DEST` | Copies a file or, with options, directory trees. | Can overwrite data and consume storage. |
| `rm FILE` | Removes a directory entry. | Destructive; recovery may be difficult. |

The video title and description explicitly frame the system-damage demonstration; the original high-impact command is intentionally not reproduced here. Consult each utility's manual before using options not shown in this safe exercise.

## Bounded practice in a disposable Kali VM

```bash
lab="$HOME/file-ops-practice"
mkdir -p "$lab"
printf '%s\n' 'practice only' > "$lab/original.txt"
cp -n "$lab/original.txt" "$lab/copy.txt"
mkdir "$lab/one-directory"
ls -la "$lab"
```

This creates two small text files and one directory under a fixed path in the home folder. `ls` lets you inspect the result. No output is claimed as a captured run. Avoid loops, recursive operations, broad wildcards, root-owned locations, and commands copied from a video until you understand their full effect.

## Common mistakes and precautions

- Assuming `>` appends; it truncates. Use `>>` only when appending is intended.
- Running commands from an unexpected working directory.
- Using `*` or recursive flags without listing the matched paths first.
- Creating unbounded numbers of files or directories; storage or inode exhaustion can make a VM unusable.
- Treating `sudo` as a safety mechanism. It increases the scope of a mistake.

## Security application

File integrity and availability depend on controlling write and deletion scope. Use least privilege, backups or VM snapshots, explicit paths, and reviewable changes. For forensic work, preserve originals and document any necessary copy or transformation.

## Revision questions

1. What is the difference between `>` and `>>`?
2. Why can a loop that creates many directories affect system availability?
3. What should you verify before using `mv`, `cp`, or `rm`?
4. Why is a disposable VM snapshot useful for learning hazardous commands?

## References

- [Episode 10 video and chapter information](https://www.youtube.com/watch?v=ugt3PBeqHIo)
- [GNU Coreutils manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [Bash manual: redirections](https://www.gnu.org/software/bash/manual/html_node/Redirections.html)
