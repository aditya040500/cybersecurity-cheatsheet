# Processes and Services

## Processes

A process is a running instance of a program. Process identifiers (PIDs) identify processes on a host. Use inspection commands to understand system state before attempting to change it.

| Command | Purpose | Example |
| --- | --- | --- |
| `ps -ef` | Inspect a process listing; `-e` selects all processes and `-f` uses a full-format listing. | `ps -ef` |
| `ps -p PID -o pid,ppid,user,stat,cmd` | Inspect selected fields for one PID. | `ps -p 1234 -o pid,ppid,user,stat,cmd` |
| `top` | Interactively inspect processes and resource use; press `q` to quit. | `top` |
| `pgrep -a NAME` | Find process IDs and command lines matching a name. | `pgrep -a ssh` |

PIDs change over time and may be reused. Verify the target and owner before taking action.

## Signals

`kill -TERM PID` requests graceful termination using the TERM signal. It modifies system state and can interrupt work. `kill -KILL PID` forces termination and prevents cleanup; avoid it unless a documented recovery procedure requires it. Never infer that a process is malicious from its name alone.

## Services with systemd

| Command | Effect | Example |
| --- | --- | --- |
| `systemctl status SERVICE` | Inspect service state and recent status details. | `systemctl status ssh` |
| `systemctl list-units --type=service` | Inspect loaded service units. | `systemctl list-units --type=service` |
| `sudo systemctl restart SERVICE` | **Elevated modify:** restart a service and may interrupt users. | Use only after impact and maintenance requirements are understood. |
| `sudo systemctl enable SERVICE` | **Elevated modify:** configure a service to start at boot. | Make only as an approved configuration change. |

Service names and service managers differ by distribution. A service being active does not establish that its configuration is secure.

## Common mistakes

- Killing a process before identifying what it does and who depends on it.
- Using force termination before attempting an orderly stop.
- Restarting a production service without checking impact and change procedures.
- Treating service status as proof that an application is healthy or secure.

## Revision points

- Inspect PID, owner, command, and service context before intervention.
- Prefer a graceful, documented action over a forced one.
- Separate "running" from "correctly configured" and "healthy."

## References

- [NetworkChuck Linux for Hackers playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
- [systemd `systemctl` manual](https://www.freedesktop.org/software/systemd/man/latest/systemctl.html)
