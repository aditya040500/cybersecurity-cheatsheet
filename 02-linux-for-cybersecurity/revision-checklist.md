# Final Revision Checklist

## Before a command

- Confirm the working directory (`pwd`), target path, current account (`id`), and command syntax (`man` or `--help`).
- Classify the command: inspect, local file change, network request, privileged change, or destructive action.
- Quote paths and variables; review shell history before re-running a command.
- Practise in a disposable Kali VM snapshot with no valuable data.

## Core Linux ideas

- `/` is the filesystem root; `/root` is commonly the root user's home. Paths and mounted filesystems vary by distribution.
- `>` truncates a destination; `>>` appends. A pipe passes standard output to another command.
- `apt update` refreshes repository metadata; it does not upgrade installed packages.
- `start` affects current service state; `enable` affects boot configuration.
- Identify a process by PID, owner, and command before signalling it. Prefer graceful termination to forced termination.
- A listener is local state; routing and firewall policy affect whether other hosts can reach it.
- `clear` hides current display content but does not erase history or logs.
- `sudo` expands impact and does not make a command safe.

## Safe file-operation checklist

Before `cp`, `mv`, redirection, or removal, verify the exact source, destination, wildcard expansion, privilege level, and recovery plan. Avoid recursive or unbounded operations while learning. Keep demonstration services bound to `127.0.0.1` unless an isolated lab requires otherwise.

## Review prompts

1. How would you inspect an unfamiliar service without changing its state?
2. What is the difference between an operating-system package and a Python project dependency?
3. Why can a process name alone be an unsafe termination target?
4. How can a command-line shortcut make work faster but less safe?
