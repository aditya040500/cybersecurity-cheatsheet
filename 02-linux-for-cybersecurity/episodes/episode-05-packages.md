# Episode 5: Linux Package Management

**Video:** [apt, dpkg, git, Python PiP (Linux Package Management) // EP 5](https://www.youtube.com/watch?v=vX3krP6JmOY)
**Source evidence:** The public description and chapter markers cover Debian packages, `dpkg`, APT repositories, `apt update`, installed packages, removal, upgrades, `aptitude`, Snap, Python `pip`, RubyGems, Git, `git clone`, and requirements files.
**Practice level:** Inspection examples are safe; installations and upgrades modify the VM and use elevated access.

## Learning objectives

- Distinguish a package archive from a repository-aware package manager.
- Check package source and proposed system changes before installation.
- Keep Python project dependencies separate from OS packages where possible.

## Command reference

| Syntax | Purpose | Change level |
| --- | --- | --- |
| `apt show PACKAGE` | Inspect package metadata from configured sources. | Read-only |
| `dpkg -l PATTERN` | List local package database entries matching a pattern. | Read-only |
| `sudo apt update` | Refresh local package indexes; does not itself upgrade installed packages. | Elevated; writes index data and contacts repositories |
| `sudo apt install PACKAGE` | Install a package and dependencies from configured sources. | Elevated system change |
| `sudo dpkg -i FILE.deb` | Install a local Debian package archive. | Elevated system change; dependencies may need repair |
| `git clone URL DIR` | Copy a remote repository into a new local directory. | Network and local filesystem change |
| `python3 -m venv .venv` | Create a project-local Python environment. | Local filesystem change |
| `python -m pip install -r requirements.txt` | Install dependencies listed in a project file into the active environment. | Package installation; review sources and versions first |

## Safe practice in a Kali VM

```bash
apt show curl
dpkg -l 'curl'
python3 -m venv "$HOME/linux-practice/.venv"
```

The first two commands inspect package information; the final command creates an isolated environment in the practice folder. To install software, first verify the repository configuration and review APT's proposed actions. Never use `sudo pip` as a routine fix for an environment conflict.

## Common mistakes

- Treating `apt update` as an upgrade; it refreshes repository indexes.
- Downloading and installing a `.deb` from an unverified source.
- Running a repository's dependency file without reviewing package names and origins.
- Mixing project Python packages with distribution-managed Python packages.
- Cloning an untrusted repository and executing its install script without review.

## Security application

Package management is part of patching and software provenance. Use trusted repositories, minimize installed software, review updates for service impact, and preserve enough version information to investigate changes.

## Revision questions

1. What does `apt update` change, and what does it not do?
2. How does `dpkg -i` differ from `apt install`?
3. Why use a virtual environment for a Python project?
4. What should be checked before cloning and running code from a repository?

## References

- [Episode 5 video and chapters](https://www.youtube.com/watch?v=vX3krP6JmOY)
- [APT manual](https://manpages.debian.org/apt/apt.8.en.html)
- [dpkg manual](https://manpages.debian.org/dpkg/dpkg.1.en.html)
- [Python `venv`](https://docs.python.org/3/library/venv.html)
