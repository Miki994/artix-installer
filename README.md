# artix-installer

A stupid installer for Artix Linux

## Usage

1. Run `./install.sh`.
2. When everything finishes, `poweroff`.

## Assumptions

* These scripts assume you are already booted into the Artix live disk or you at least have `artools` on your system and have loaded all of the scripts in some way. These scripts can be loaded with `git`, another USB drive, or perhapts `wget`.
* It also assumes you want what it wants and adhere to the occasional instructions it gives you, the user, to perform.
* You're aware that you'll manually have to enter `--type luks1` as a luks option until GRUB gets upgraded from 2.0.4

## What you get

An encrypted Artix Linux system with OpenRC and Btrfs subvols for root, snapshots, and home. Only necessary packages are installed with a few minor exceptions for flavor or the install process (`python`, `zsh`, `neovim`, `neofetch`).

Post-installation networking is done with `connman`.

### Partition Scheme
\# | Size | Type | LUKS | FS
-|-|-|-|-
1 | 1G | EFI System |  | fat32
2 | ~4G | Linux swap | * | swap
3 | FREE | Linux filesystem | * | btrfs

### Btrfs subvolumes
\# | Name | Mount
-|-|-
1 | @ | /
2 | @snapshots | /.snapshots
3 | @home | /home

### Software
Feature | Name
-|-
Boot loader | GRUB
Filesystem | Btrfs
Init Software | OpenRC
Networking | connman
Shell | Zsh
