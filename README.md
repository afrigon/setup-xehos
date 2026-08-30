# setup-xehos

Bootstrap for my personal machines, part of AXR.

## What it does

`setup-xehos` prepares a machine for daily use, as a regular user:

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
`mise` must be installed — on Arch the `base-xehos` metapackage provides
both, on macOS Homebrew does.

## Fresh-machine flow (Arch)

Enable the [axr](https://github.com/afrigon/axr) repository:

```sh
sudo pacman -U https://axr.frigon.app/axr-keyring.pkg.tar.zst
```

Add it to `/etc/pacman.conf`:

```ini
[axr]
SigLevel = Optional
Server = https://axr.frigon.app/$arch
```

Install [paru](https://github.com/Morganamilo/paru):

```sh
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg --syncdeps --install
```

Install and run the bootstrap:

```sh
paru -S setup-xehos
setup-xehos
```

The `setup-xehos` package is built by the PKGBUILD in the
[axr](https://github.com/afrigon/axr) repository from a tagged release of
this repository.

## Fresh-machine flow (macOS)

Install [Homebrew](https://brew.sh), then:

```sh
brew install git mise
curl -fsSL https://raw.githubusercontent.com/afrigon/setup-xehos/main/setup-xehos | sh
```
