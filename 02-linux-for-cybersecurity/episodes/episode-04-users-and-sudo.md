# Episode 4: Users, Groups, and `sudo`

**Video:** [sudo = POWER!! (managing users in Linux) // EP4](https://www.youtube.com/watch?v=jwnvKOjmtEA)
**Source evidence:** The video description and chapter markers explicitly cover `adduser`, `/etc/passwd`, `/etc/shadow`, `useradd`, `passwd`, `usermod`, `sudo`, `su`, `visudo`, `userdel`, groups, and `gpasswd`.
**Practice level:** Inspect identity only. User and privilege changes require a disposable VM and administrator authorization.

## Learning objectives

- Distinguish user identity, group membership, and privileged execution.
- Locate account database files and understand why password hashes are protected.
- Explain the risk of broad `sudo` access and the purpose of `visudo`.

## Commands and files

| Syntax | Purpose | Impact |
| --- | --- | --- |
| `whoami`; `id USER` | Inspect effective identity or a user's numeric/name IDs and groups. | Read-only |
| `getent passwd USER` | Query the configured account database. | Read-only; output is account metadata. |
| `getent group GROUP` | Query group data. | Read-only |
| `sudo COMMAND` | Request one command with elevated privileges under local policy. | Depends on command; often high impact |
| `su - USER` | Start a login shell as another user, subject to policy and credentials. | Changes the active shell identity |
| `sudo visudo` | Edit sudo policy with syntax validation and locking. | Privileged configuration change |
| `usermod -aG GROUP USER` | Append a user to supplementary group membership. | Privileged account change |

`/etc/passwd` contains account records, not normally password hashes. `/etc/shadow` stores protected password authentication data and should not be exposed. Modern systems may use additional identity sources. Prefer the documented account-management tools rather than editing these files directly.

## Safe practice in a Kali VM

```bash
whoami
id
getent passwd "$(whoami)"
sudo -l
```

The commands inspect the current user and the sudo permissions granted by local policy; `sudo -l` may request authentication. Output is host-specific and can reveal account details, so do not publish it unreviewed. Do not create users or change groups on a shared system as practice.

## Common mistakes

- Confusing authentication (proving identity) with authorization (permitted actions).
- Forgetting `-a` in `usermod -aG`; without append mode, supplementary groups can be replaced.
- Giving routine accounts unnecessary administrator privileges.
- Editing sudo policy with a plain editor rather than the validation-capable `visudo`.
- Assuming a successful `sudo` command makes the underlying action safe.

## Security application

Use unique accounts, least privilege, limited elevation, and auditable changes. Review group membership and sudo rules after role changes or suspected account compromise.

## Revision questions

1. What question does authentication answer? What question does authorization answer?
2. What information is normally in `/etc/passwd` versus `/etc/shadow`?
3. Why is `usermod -aG` different from `usermod -G`?
4. Why should sudoers changes be made through `visudo`?

## References

- [Episode 4 video and chapters](https://www.youtube.com/watch?v=jwnvKOjmtEA)
- [`usermod` manual](https://man7.org/linux/man-pages/man8/usermod.8.html)
- [`sudoers` manual](https://www.sudo.ws/docs/man/sudoers.man/)
