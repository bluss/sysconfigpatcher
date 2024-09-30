
## 0.3.1

- Accept path to bin/python or bin/python3 in addition to install root for specifying
  python installation to patch.

## 0.3.0

- Add the following to default variables updated for compiler name (from clang to cc):
  `BLDSHARED`, `LDSHARED`, `LDCXXSHARED`, `LINKCC`

## 0.2.0

- Support macos (fix fdatasync call that was not supported)
- Replace clang in CXX variable too and tweak how it was replaced in CC
- Update pyproject.toml to use uv instead of rye for project management

## 0.1.0

- Initial release
