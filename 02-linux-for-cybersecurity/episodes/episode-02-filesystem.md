# Episode 2: The Linux Filesystem

**Video:** [The Linux File System explained in 1,233 seconds // EP 2](https://www.youtube.com/watch?v=A3G-3hp88mo)
**Source evidence:** The public title and description identify the Linux filesystem; an indexed episode summary describes the root of the tree, the "everything is a file" model, and navigation. The description says the video introduces seven command-line commands.
**Practice level:** Inspect the VM filesystem; do not edit system files.

## Learning objectives

- Read a Linux path from the filesystem root.
- Recognize common top-level directories and their typical purpose.
- Use file-oriented inspection commands without confusing file types with safety.

## Concepts

Linux presents filesystems through one directory tree rooted at `/`. Devices and kernel interfaces may be exposed through filesystem-like paths, but not every path behaves like an ordinary disk file. Directory names such as `/etc`, `/home`, `/tmp`, `/usr`, `/var`, `/dev`, `/proc`, and `/sys` have conventional roles; exact layout and mounted filesystems vary by distribution.

| Path or command | Purpose / behavior | Example |
| --- | --- | --- |
| `/` | Root of the directory tree. | `ls -la /` |
| `/etc` | System-wide configuration, generally not personal documents. | `ls /etc` |
| `/home` | Home directories for regular users on many systems. | `ls /home` |
| `/var` | Variable data such as logs, caches, and service state. | `ls /var/log` |
| `file PATH` | Infers a file type from content and metadata. | `file /etc/hosts` |
| `stat PATH` | Shows filesystem metadata such as size, mode, and timestamps. | `stat /etc/hosts` |

## Safe practice in a Kali VM

```bash
ls -la /
ls -ld /etc /home /tmp /var
file /etc/hosts
stat /etc/hosts
```

Expected behavior: listings show entries available to the VM user; `file` reports a likely type and `stat` reports metadata. Exact values vary across systems. These commands inspect only.

## Common mistakes

- Treating `/root` as the same as `/` (`/root` is commonly root's home directory).
- Assuming every file-like path stores ordinary persistent data.
- Editing a system configuration file just to explore its contents.
- Treating `file` output as a malware verdict; file-type identification is not a safety analysis.

## Security application

Knowing standard locations helps an analyst find configuration, logs, user data, and device information while preserving scope. Record the path and relevant metadata before making an authorized change.

## Revision questions

1. What does the leading `/` indicate in an absolute path?
2. Which kinds of information are commonly found under `/etc` and `/var`?
3. Why is "everything is a file" a useful model but not a literal guarantee?
4. Does `file sample` determine whether `sample` is safe?

## References

- [Episode 2 video](https://www.youtube.com/watch?v=A3G-3hp88mo)
- [Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
- [GNU Coreutils manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
