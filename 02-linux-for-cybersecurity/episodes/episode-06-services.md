# Episode 6: Services and `systemd`

**Video:** [Start, stop, restart Linux services (daemon HUNTING!!) // EP 6](https://www.youtube.com/watch?v=wOWhfNB_r-0)
**Source evidence:** The indexed description says the episode covers starting, stopping, restarting, and enabling services. Its chapter markers identify daemons, systemd, `systemctl`, service status, boot enablement, hunting services, and troubleshooting.
**Practice level:** Status and listing are inspection; start/stop/restart/enable are state changes.

## Learning objectives

- Explain the difference between a process, a daemon, a service, and a systemd unit.
- Inspect service state before taking action.
- Distinguish running now (`start`) from starting during boot (`enable`).

## Command reference

| Syntax | Behavior | Impact |
| --- | --- | --- |
| `systemctl status UNIT` | Show unit state and recent status information. | Inspect |
| `systemctl list-units --type=service` | List currently loaded service units. | Inspect |
| `sudo systemctl start UNIT` | Start a service now. | State change; can open a listener or consume resources |
| `sudo systemctl stop UNIT` | Stop a service now. | State change; can interrupt dependent work |
| `sudo systemctl restart UNIT` | Stop and start a service. | State change; brief outage or lost sessions possible |
| `sudo systemctl enable UNIT` | Configure a unit to start automatically at boot. | Persistent configuration change |
| `systemctl is-enabled UNIT` | Inspect boot enablement state. | Inspect |

## Safe practice in a Kali VM

```bash
systemctl status ssh
systemctl list-units --type=service --state=running
systemctl is-enabled ssh
```

These commands inspect local units; output differs between Kali installations. Do not enable or expose a remote-access service merely to practise. If testing state changes, snapshot the VM and use a service you understand, then restore the original state.

## Common mistakes

- Assuming a service named `ssh` exists or uses the same unit name on every distribution.
- Confusing `start` with `enable`.
- Restarting a service without considering users, dependencies, logs, or recovery.
- Treating an "active" status as proof that the service is correctly configured or externally reachable.

## Security application

Inventory active services and compare them with an approved baseline. Disable unnecessary services only through a controlled change; confirm listening sockets and firewall exposure separately.

## Revision questions

1. What is a daemon, and how does it relate to a service unit?
2. Which `systemctl` operation affects the current session? Which affects future boots?
3. Why might `systemctl status` succeed while the service is still insecure?
4. What should be checked before stopping a production service?

## References

- [Episode 6 video and chapters](https://www.youtube.com/watch?v=wOWhfNB_r-0)
- [`systemctl` manual](https://www.freedesktop.org/software/systemd/man/latest/systemctl.html)
- [systemd unit concepts](https://www.freedesktop.org/software/systemd/man/latest/systemd.unit.html)
