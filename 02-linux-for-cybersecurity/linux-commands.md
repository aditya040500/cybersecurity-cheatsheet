# Linux Command Reference

Use commands with the permissions needed for the task only. Arguments beginning with `-` are options; quoting protects paths containing spaces from shell word splitting.

## Inspect the current location

| Command | Purpose | Safe example |
| --- | --- | --- |
| `pwd` | Print the current working directory. | `pwd` |
| `whoami` | Print the effective user name. | `whoami` |
| `id` | Show the effective identity and group memberships. | `id` |
| `date -Is` | Show the current time in ISO-like format. | `date -Is` |

These commands inspect state and do not change files. Output depends on the host and account.

## List and search

| Command | Purpose and arguments | Safe example |
| --- | --- | --- |
| `ls -la PATH` | List entries; `-l` uses a detailed listing and `-a` includes dotfiles. | `ls -la "$HOME"` |
| `find PATH -type f -name PATTERN` | Search recursively; `-type f` selects files and `-name` matches a name pattern. | `find "$HOME/Documents" -type f -name '*.log'` |
| `grep -n 'TEXT' FILE` | Search file text; `-n` includes line numbers. | `grep -n 'failed' auth.log` |
| `wc -l FILE` | Count newline-delimited lines. | `wc -l auth.log` |

Searching a broad tree can take time and may produce permission errors. Search only paths you are authorized to inspect.

## Read files

| Command | Purpose | Safe example |
| --- | --- | --- |
| `cat FILE` | Write the file contents to standard output. | `cat notes.txt` |
| `less FILE` | Read a file interactively; press `q` to quit. | `less /var/log/syslog` |
| `head -n N FILE` | Show the first N lines. | `head -n 20 auth.log` |
| `tail -n N FILE` | Show the last N lines. | `tail -n 20 auth.log` |
| `tail -f FILE` | Follow appended data until interrupted with Ctrl+C. | `tail -f app.log` |

Log locations and access permissions vary by distribution. Do not copy sensitive log data into an unapproved location.

## Pipes and redirection

| Syntax | Effect | Example |
| --- | --- | --- |
| `A \| B` | Send A's standard output to B's standard input. | `grep 'failed' auth.log \| wc -l` |
| `A > FILE` | Replace FILE with A's standard output. | `printf '%s\n' 'review' > review.txt` |
| `A >> FILE` | Append standard output to FILE. | `date -Is >> review.txt` |
| `A 2> FILE` | Redirect standard error. | `find /var/log -type f 2> find-errors.txt` |
| `A && B` | Run B only if A exits successfully. | `mkdir review && cd review` |

`>` overwrites its destination. Verify the path before using redirection. A pipeline generally passes output, not the first command's success status, unless shell options are configured.

## Change or create files

Commands that modify the filesystem are marked **Modify**. Check paths before acting.

| Command | Purpose and arguments | Safe example |
| --- | --- | --- |
| `mkdir -p PATH` | **Modify:** create directories; `-p` also creates missing parents and does not fail if the directory exists. | `mkdir -p "$HOME/lab-notes"` |
| `touch FILE` | **Modify:** create an empty file or update timestamps. | `touch "$HOME/lab-notes/todo.txt"` |
| `cp SOURCE DEST` | **Modify:** copy a file. | `cp notes.txt notes.backup.txt` |
| `mv SOURCE DEST` | **Modify:** move or rename; an existing destination may be replaced depending on options and prompting configuration. | `mv draft.txt draft-reviewed.txt` |
| `rm FILE` | **Destructive:** remove a directory entry; there is usually no simple undo. | Avoid in routine study examples; confirm exact target and backups first. |

Avoid recursive deletion options during exploration. Shell wildcards can expand to more files than intended. Inspect the exact target with `printf '%s\n' PATH` or `ls` before any removal.

## Revision points

- `pwd`, `ls`, and `cd` are the core navigation commands highlighted in the accessible episode 1 chapters.
- Inspect before changing; quote variable paths; check permissions and scope.
- `>` overwrites, `>>` appends, and pipes connect command output.
- Treat `rm`, recursive options, and privileged commands as high-impact operations.

## References

- [NetworkChuck Linux for Hackers playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
- [Episode 1 with chapter markers](https://www.youtube.com/watch?v=VbEx7B_PTOE)
- [Coreutils command index](https://man7.org/linux/man-pages/man1/coreutils.1.html)
- [grep manual](https://man7.org/linux/man-pages/man1/grep.1.html)
