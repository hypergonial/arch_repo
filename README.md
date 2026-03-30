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
> 
