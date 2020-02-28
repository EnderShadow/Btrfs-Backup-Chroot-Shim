# Btrfs-Backup-Chroot-Shim
A small python program that is meant to replace btrfs in chroot such that only backup related commands are allowed to be executed as root. This is only meant to be used as an indrection for /usr/bin/btrfs when you have a rule in your sudoers file that allows the btrfs program to be run as root without a password.

## Requirements
- Python 3
- An existing chroot environment

## Installation
Everything in this section will specify files and directories relative to the chroot you are using for this.

1. Rename /usr/bin/btrfs to /usr/bin/btrfs.real
2. Copy the btrfs file in this repository to /usr/bin/btrfs
3. Change the owner of /usr/bin/btrfs to root:root and set the permissions to 755
4. Add `ALL ALL=(root) NOPASSWD: /usr/bin/btrfs` to /etc/sudoers or in it's own file in /etc/sudoers.d/

Now anyone chrooted into your chroot environment will be able to run the following btrfs commands as root without a password
- `btrfs send`
- `btrfs receive`
- `btrfs property`
- `btrfs subvolume create`
- `btrfs subvolume delete`
- `btrfs subvolume show`
- `btrfs subvolume snapshot`
- `btrfs subvolume sync`
