# setup-xehos

Machine bootstrap for Arch workstations, part of AXR.

## What it does

`setup-xehos` prepares a workstation for daily use, as a regular user:

- clones https://github.com/afrigon/dotfiles into `~/src/dotfiles` if it
  is not already there
- runs `mise trust` and `mise run bootstrap` in that repo, which stows
  config into `~/.config` and installs mise-managed tools

It is safe to re-run on an already-bootstrapped machine.

## Usage

```sh
setup-xehos
```

Run as a regular user; the script refuses to run as root. `git` and
`mise` must be installed — the `base-xehos` metapackage provides both.

## Fresh-machine flow

Documented in the [axr](https://github.com/afrigon/axr) repository:
install the axr keyring and repository, bootstrap paru, then
`paru -S setup-xehos`.

The `setup-xehos` package is built by the PKGBUILD in the
[axr](https://github.com/afrigon/axr) repository from a tagged release of
this repository.
