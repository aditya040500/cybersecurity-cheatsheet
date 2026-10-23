# Package Management

The accessible playlist feed includes an episode titled "apt, dpkg, git, Python PiP (Linux Package Management)." Package commands differ across distributions. The examples below use Debian-family `apt` and `dpkg`; use the package manager documented for the host.

## Inspect installed and available packages

| Command | Effect | Safe example |
| --- | --- | --- |
| `apt show PACKAGE` | Inspect package metadata available to configured sources. | `apt show curl` |
| `dpkg -l PATTERN` | Inspect locally known package status; `-l` requests a listing. | `dpkg -l 'openssh*'` |
| `dpkg -S PATH` | Find which installed package owns a path. | `dpkg -S /usr/bin/ssh` |
| `apt list --installed` | List installed packages. | Output may be lengthy; pipe to a search only when useful. |

## Update and install

| Command | Effect | Precautions |
| --- | --- | --- |
| `sudo apt update` | **Elevated modify:** refresh package indexes from configured repositories; does not itself upgrade installed packages. | Verify repository configuration and use an authorized host. |
| `sudo apt install PACKAGE` | **Elevated modify:** install a package and required dependencies. | Review the proposed package changes before confirming. |
| `sudo apt upgrade` | **Elevated modify:** upgrade installed packages according to local APT behavior. | Can change services or dependencies; follow change and maintenance procedures. |
| `sudo dpkg -i FILE.deb` | **Elevated modify:** install a local Debian package file. | Verify provenance and integrity; handle dependencies through the package manager. |

Package operations access configured repositories and change the host. Do not install tools on systems without authorization. Avoid piping downloaded scripts directly into a privileged shell.

## Python packages

Use a virtual environment for project-specific Python dependencies. This limits package changes to the project environment and helps avoid conflicts with operating-system-managed Python packages.

```text
python3 -m venv .venv
. .venv/bin/activate
python -m pip install PACKAGE
python -m pip show PACKAGE
```

The first three commands create and activate a project environment and install a named package; `pip show` inspects package metadata. Package names and dependencies should be reviewed before installation. Do not use `sudo pip` as a routine workaround for permission errors.

## Git basics

Git is a version-control tool, not a system package manager. The following commands inspect local repository state:

| Command | Purpose |
| --- | --- |
| `git --version` | Show the installed Git version. |
| `git status` | Inspect the current repository's changes and branch state. |
| `git log --oneline -5` | Inspect the latest five commits in compact form. |

Cloning or fetching contacts a remote and writes repository data locally. Confirm the remote source and destination path before using network operations.

## Revision points

- `apt` manages repository packages on Debian-family distributions; `dpkg` works with local package database and package files.
- Refreshing package indexes is different from upgrading installed software.
- Package installation and upgrades change the host and usually require elevation.
- Keep Python project dependencies in a virtual environment; use Git to track project changes.

## References

- [NetworkChuck Linux for Hackers playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
- [APT manual](https://manpages.debian.org/apt/apt.8.en.html)
- [dpkg manual](https://manpages.debian.org/dpkg/dpkg.1.en.html)
- [Python `venv` documentation](https://docs.python.org/3/library/venv.html)
- [pip documentation](https://pip.pypa.io/en/stable/)
