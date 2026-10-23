# Help and Terminal Workflow

The playlist feed includes an episode titled "HELP!! (for when you suck at Linux)" and a terminal-shortcuts video. This page collects safe ways to find command help and work efficiently in a shell; exact lesson demonstrations were not available for verification.

## Find command documentation

| Command | Purpose | Example |
| --- | --- | --- |
| `man COMMAND` | Open the installed manual page; press `q` to quit. | `man ls` |
| `COMMAND --help` | Show command-specific usage when supported. | `cp --help` |
| `apropos KEYWORD` | Search manual-page names and short descriptions. | `apropos permissions` |
| `type COMMAND` | Show how the shell resolves a command name. | `type cd` |
| `command -v COMMAND` | Print the executable path or shell resolution where available. | `command -v python3` |

Manual-page sections can contain the same name for different interfaces; use `man SECTION NAME` when the target is ambiguous. Examples include `man 1 printf` for the shell command and `man 3 printf` for a C library function.

## Shell history and editing

| Action | Effect | Caution |
| --- | --- | --- |
| Up / Down arrow | Recall earlier or later commands in the current shell history. | Review a recalled command before pressing Enter. |
| Tab | Complete a command or path when the shell can identify a match. | Multiple matches may require another Tab or more characters. |
| Ctrl+C | Send an interrupt to the foreground process. | May interrupt a command that is changing data; understand what is running. |
| Ctrl+L | Clear the visible terminal area in common shells. | This clears the display, not shell history or logs. |
| `history` | Show commands recorded in the shell history. | History can contain sensitive values; avoid putting secrets directly in commands. |

## Safer command habits

- Read the command and arguments before pressing Enter, especially after using history completion.
- Use `man` or `--help` to check flags before combining options.
- Quote paths and variables that may contain spaces or shell metacharacters.
- Avoid placing passwords, tokens, or other secrets in command arguments; shells may retain them in history or expose them to process listings.
- Use `clear` or Ctrl+L only to manage the display; do not mistake it for secure deletion.

## Revision points

- Prefer the local manual page for distribution-specific details.
- Check a command's target and flags before running it with elevated privileges.
- Shell history and process listings can expose sensitive command-line values.

## References

- [NetworkChuck Linux for Hackers playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
- [Bash manual](https://man7.org/linux/man-pages/man1/bash.1.html)
