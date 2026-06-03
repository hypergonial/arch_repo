# Mullvad + Tailscale Split Tunnel

A tiny package that ships two [nftables](https://wiki.archlinux.org/title/Nftables) rulesets: [mullvad-ts.rules](./mullvad-ts.rules) and [mullvad-ts-cleanup.rules](./mullvad-ts-cleanup.rules), to be used with [Mullvad](https://mullvad.net/en) and [Tailscale](https://tailscale.com/) to split tunnel traffic.

The first ruleset is loaded when Tailscale is up, and torn down via the second ruleset when Tailscale goes down. It marks all traffic that goes through Tailscale with Mullvad's mark and metamark as documented in <https://mullvad.net/en/help/split-tunneling-with-linux-advanced>.

Without this, Mullvad's kill switch will block all Tailscale traffic, since it doesn't know about Tailscale's routes and interfaces. With the package installed however, you can have both Mullvad and Tailscale running at the same time without conflicts.

## Usage

```bash
pacman -S mullvad-tailscale-split-tunnel
sudo systemctl daemon-reload
```

## Releasing

- Make your changes and commit them to the `main` branch
- Update the `VERSION` file with a new version number
- CI will automatically bump the `pkgver`/`pkgrel` and build the package
