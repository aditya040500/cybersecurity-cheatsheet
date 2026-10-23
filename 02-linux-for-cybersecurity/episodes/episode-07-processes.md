# Episode 7: Process Management

**Video:** [KILL Linux processes!! (also manage them) // EP 7](https://www.youtube.com/watch?v=LfC6pv8VISk)
**Source evidence:** The public description states that the episode covers finding processes, moving them between foreground and background, and terminating them.
**Practice level:** Listing is inspection; signals and job-control actions alter process state.

## Learning objectives

- Identify a process by PID, command, owner, and parent process.
- Understand foreground/background jobs and signals.
- Prefer graceful termination and verify the target before sending a signal.

## Command reference

| Syntax | Purpose | Impact |
| --- | --- | --- |
| `ps -ef` | List processes; `-e` selects all, `-f` uses full format. | Inspect |
| `pgrep -a NAME` | Find matching PIDs and command lines. | Inspect |
| `jobs -l` | List jobs started by the current shell. | Inspect |
| `COMMAND &` | Start a command asynchronously in the shell. | Starts a process |
| `fg %N`; `bg %N` | Bring a shell job to foreground or continue it in background. | Alters job state |
| `kill -TERM PID` | Request orderly termination with TERM. | May interrupt work |
| `kill -KILL PID` | Force immediate termination; process cannot handle cleanup. | High impact; last resort |

## Safe practice in a Kali VM

```bash
sleep 300 &
jobs -l
pgrep -a sleep
```

This starts a harmless timer in the current VM. To stop only the timer you started, identify its PID from `jobs -l`, then use `kill -TERM PID` and verify it exited. The literal `PID` is a placeholder: replace it with the verified numeric process ID. Do not copy a guessed PID.

## Common mistakes

- Sending a signal based only on a process name; multiple unrelated processes may match.
- Using `kill -9` before trying graceful termination.
- Forgetting PIDs can be reused after a process exits.
- Confusing shell jobs with all system processes.

## Security application

During investigation, preserve process context: executable path, owner, parent, arguments, start time, and related network connections. In an incident, coordinate termination with evidence-preservation and containment procedures.

## Revision questions

1. What fields help you confirm that a process is the intended target?
2. How does `TERM` differ from `KILL`?
3. What does `&` do in a shell command?
4. Why should an analyst collect process context before terminating a suspicious process?

## References

- [Episode 7 video](https://www.youtube.com/watch?v=LfC6pv8VISk)
- [`ps` manual](https://man7.org/linux/man-pages/man1/ps.1.html)
- [`kill` manual](https://man7.org/linux/man-pages/man1/kill.1.html)
