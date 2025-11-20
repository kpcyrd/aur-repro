aur-repro
=========

Reproducible Builds for packages in the [Arch User Repository
(AUR)](https://aur.archlinux.org/). Fork of
[`archlinux-repro`](https://github.com/archlinux/archlinux-repro).

The current goals are:
- Recreate packages given a `.BUILDINFO` file, or `.pkg.tar.zst`
- Locate and fetch the correct `PKGBUILD` from `aur.archlinux.org`
- Download and verify needed packages from `archive.archlinux.org`
- Distribution independent. One should be able to verify AUR packages on Debian.

Work in progress. Please read the code before using.

## Missing features

Patches very welcome.

- Possibly also support fetching build dependencies from a custom archive, and
  only if the package is not present there, try archive.archlinux.org

This would need to be implemented in `aur-buildinfo` (which may need to read
a configuration file in the future).

## Considerations

The AUR has a different trust model than Arch Linux itself. There might be
unexpected implications that haven't been explored yet.

For the time being, the following are known:

- If custom dependencies are installed from a third party repository, they
  might modify the build environment in unexpected ways (e.g. by placing
  configuration files into the build users home directory), reviewing the
  PKGBUILD and referenced source code is not sufficient anymore.
    - For this reason, a user may chose to rebuild a repository but only allow
      dependencies on official Arch Linux packages

## Dependencies

* asciidoc (make)
* coreutils
* curl
* gnupg
* systemd
* bsdtar
* zstd
