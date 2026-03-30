# Example package

This is an example to demonstrate how to add a package to this repository. You can use this as a template for adding your own packages to the repository.

## Structure

### PKGBUILD

This is an Arch Linux `PKGBUILD` file, which is used to define how to build and package the software. The `PKGBUILD` file should be a valid [PKGBUILD](https://wiki.archlinux.org/title/PKGBUILD).

The `pkgver`, `pkgrel`, and `sha256sums` fields are updated automatically by the CI when a new version is detected, so they should initially be set to `0.0.0`, `0`, and `SKIP` respectively.

The `sha256sums` field should only be updated manually via `updpkgsums` if you change the `source` array of an existing package, for example if you change the URL or add new source files. If you are adding a new package, you can just leave it as `SKIP` and the CI will update it when a new version is detected.

### PKGUPDATE

The `PKGUPDATE` file is a custom script used by the CI to check for new versions of the package. It should define a `get_latest_version` function that returns the latest version of the software as a string. The CI will call this function and compare the returned version with the current `pkgver` in the `PKGBUILD`. If a version mismatch is detected, the CI will update the `pkgver`, `pkgrel`, and `sha256sums` fields in the `PKGBUILD` accordingly, build the package, and publish the new package version to the [repository](https://github.com/hypergonial/arch_repo/releases/current).

## Testing

It is recommended to build the package locally using `makepkg` to ensure that it builds correctly before pushing it to the repository.
