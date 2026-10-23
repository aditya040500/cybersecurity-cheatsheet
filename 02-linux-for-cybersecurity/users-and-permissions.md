# Users and Permissions

## Identities and groups

Processes run with user and group identities. Group membership can grant access to shared files or devices. Use `whoami` to inspect the effective user, `id` to inspect numeric and named identity/group information, and `groups` to list group memberships.

## Permission model

For each filesystem object, traditional Unix permissions define read (`r`), write (`w`), and execute (`x`) access for the owner, group, and others.

| Object | Read | Write | Execute |
| --- | --- | --- | --- |
| Regular file | Read contents | Change contents | Run as a program/script if other requirements are met |
| Directory | List names | Create, remove, or rename entries (subject to other controls) | Traverse/search the directory |

The meaning of directory permissions differs from file permissions. A directory may need execute permission to traverse it even when its names are visible.

## Inspect and change permissions

| Command | Purpose | Example |
| --- | --- | --- |
| `ls -l FILE` | Inspect owner, group, and permission bits. | `ls -l notes.txt` |
| `stat FILE` | Inspect detailed metadata. | `stat notes.txt` |
| `chmod MODE FILE` | **Modify:** change permission bits. | `chmod 640 report.txt` grants owner read/write, group read, and others none. |
| `chown USER:GROUP FILE` | **Elevated modify:** change ownership; often requires administrator rights. | Use only under an approved change plan. |
| `sudo COMMAND` | Request execution with elevated privileges under local policy. | `sudo systemctl status ssh` (read-only status operation). |

Numeric `chmod` values add permission bits: read=4, write=2, execute=1. `640` therefore means owner `6` (read+write), group `4` (read), others `0` (none). Confirm the intended access before changing permissions.

## Least privilege

Use the narrowest account and permission set that supports the task. Avoid making files globally writable or running an interactive session as root. Elevated access increases the impact of mistakes and should be limited, auditable, and authorized.

## Common mistakes

- Applying `chmod 777` as a quick fix, granting everyone read, write, and execute access.
- Confusing file write permission with permission to remove its directory entry.
- Assuming `sudo` makes a command safe or reversible.
- Changing ownership recursively without a verified target and change plan.

## Revision points

- Inspect user, groups, owner, and mode before diagnosing access.
- Understand `rwx` separately for owner, group, and others.
- Make the smallest permission change needed; use elevation only when required.

## References

- [NetworkChuck Linux for Hackers playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
- [chmod manual](https://man7.org/linux/man-pages/man1/chmod.1.html)
- [chown manual](https://man7.org/linux/man-pages/man1/chown.1.html)
