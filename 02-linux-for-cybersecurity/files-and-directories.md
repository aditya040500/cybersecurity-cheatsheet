# Files and Directories

## Navigation model

Linux uses a single directory tree rooted at `/`. A path beginning with `/` is absolute; a relative path is interpreted from the current directory. `.` means the current directory, `..` its parent, and `~` commonly expands to the current user's home directory.

| Command | Behavior | Safe example |
| --- | --- | --- |
| `pwd` | Inspect current directory. | `pwd` |
| `ls -la PATH` | Inspect contents, including hidden entries. | `ls -la /etc` |
| `cd PATH` | Change the current shell directory. | `cd "$HOME/Documents"` |
| `realpath PATH` | Print a resolved absolute path when available. | `realpath ./notes.txt` |

## File operations

| Command | Effect | Example and caution |
| --- | --- | --- |
| `mkdir -p DIR` | **Modify:** create a directory and missing parents. | `mkdir -p "$HOME/labs/week-1"` |
| `touch FILE` | **Modify:** create an empty file or update timestamps. | `touch "$HOME/labs/todo.txt"` |
| `cp SRC DEST` | **Modify:** copy a file. | `cp config.txt config.txt.bak`; check whether DEST already exists. |
| `mv SRC DEST` | **Modify:** move or rename. | `mv draft.md final.md`; verify both paths first. |
| `rm FILE` | **Destructive:** remove a file entry. | Do not use until the exact path and recovery needs are checked. |

For file metadata, `stat FILE` shows details such as size and timestamps. `file FILE` reports the type inferred from content. These inspect a file; they do not prove that it is safe to open or execute.

## Reading and locating content

Use `less FILE` for interactive reading, `head -n 20 FILE` for the first lines, and `tail -n 20 FILE` for the last lines. Search a known text file with `grep -n 'pattern' FILE`. Locate files by name with `find DIR -type f -name '*.conf'`.

Avoid searching the entire filesystem without a reason. Permission restrictions can generate errors, and broad searches may be slow or expose data outside the intended scope.

## Common mistakes

- Running a relative path from the wrong working directory.
- Forgetting that dotfiles are hidden from a plain `ls` listing.
- Assuming `mv` or `cp` will always ask before replacing a destination.
- Using wildcards with modifying commands before checking what they match.

## Revision points

- Confirm the working directory and target path before modifying files.
- Use inspection commands first and quote paths containing whitespace.
- Treat deletion and overwrite behavior as irreversible until recovery is tested.

## References

- [NetworkChuck Linux for Hackers playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
- [Coreutils command index](https://man7.org/linux/man-pages/man1/coreutils.1.html)
