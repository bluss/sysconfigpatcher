# sysconfigpatcher

The Python builds from https://github.com/indygreg/python-build-standalone
come with some build-time variables hardcoded into sysconfig, and this is
not portable - they should point to where the install is actually physically located.

This script can patch:

- sysconfigdata for linux and similar systems
- pkgconfig files for linux and similar systems

Several more files contain system specific variables that might need to be updated,
but that's not implemented yet.

It's essentially an impossible task to patch everything - because the variables
record all the configurations of a python build, to reproduce that we need to recreate
a build environment.

In general, it can only patch once. It's not intended to be used
to update the location repeatedly of an install directory.

This program should not be run as superuser.


## How to use

```
sysconfigpatcher path/to/python/install
```

## How to develop

```
rye sync

# after you've added some tests you can run this:
rye test -v

# you can test update the mock install inside tests

sysconfigpatcher -v ./tests/installs/cpython@3.12.2/
```
