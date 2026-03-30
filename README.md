# Personal Arch Repository

Fine, I'll do it myself

## Usage

Add to `/etc/pacman.conf`:

```ini
[hypergonial]
# TODO: Change this to `Required` once I bother doing signing
SigLevel = Never
Server = https://arch.hypergonial.com/repo
```

> [!NOTE]
> `https://arch.hypergonial.com/repo` is actually just a redirect for `https://github.com/hypergonial/arch_repo/releases/download/current`, both work as the server URL.

## Adding packages

Any top-level directory with a `PKGBUILD` and `PKGUPDATE` file is considered a package. The `PKGBUILD` file should be a valid [PKGBUILD](https://wiki.archlinux.org/title/PKGBUILD), the `PKGUPDATE` file is bespoke to this repository and is used to determine how to check for new versions of the package.

An example package is provided in the [`example`](./example) directory as a template. You can copy this directory and modify the `PKGBUILD` and `PKGUPDATE` files to add your own package.

> [!NOTE]
> The `pkgver` and `pkgrel` fields should initially be set to `0.0.0` and `0` respectively, as these are updated automatically by the CI when a new version is detected.
