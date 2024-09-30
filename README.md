# sysconfigpatcher

The Python builds from https://github.com/indygreg/python-build-standalone
come with some build-time variables hardcoded into sysconfig, and this is
not portable - they should point to where the install is actually physically located.

This script can patch:

- sysconfigdata
- pkgconfig files

The script seems to work on these (more information needed):

- linux
- macos

Several more files contain system specific variables that might need to be updated,
but that's not implemented yet.

It's essentially an impossible task to patch everything - because the variables
record all the configurations of a python build, to reproduce that we need to recreate
a build environment.

In general, it can only patch once. It's not intended to be used
to update the location repeatedly of an install directory.

This program should not be run as superuser.

## How to Install

Use Uv:

```bash
uv tool install 'git+https://github.com/bluss/sysconfigpatcher'
```

Or use other equivalent python tool to install sysconfigpatcher from git.


## How to use

```bash
sysconfigpatcher path/to/python/install
```

For example it could be:

```bash
sysconfigpatcher ~/.local/share/uv/python/cpython-3.12.5-macos-aarch64-none
# or
sysconfigpatcher ~/.local/share/uv/python/cpython-3.12.5-macos-aarch64-none/bin/python3
```

## How to develop

```
uv sync

# after you've added some tests you can run this:
uv run pytest

# you can test update the mock install inside tests

uv run sysconfigpatcher -v ./tests/installs/cpython@3.12.2/
```
