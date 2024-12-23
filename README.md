# GRUB 2.12 Argon2 compiled modules and config

Add LUKS2 Argon2 support to your existing GRUB2 installation without having to reinstall GRUB2.

Source/License: <https://aur.archlinux.org/packages/grub-improved-luks2-git>

## Installation (x86-64)

If you don't want to compile it yourself, all you need to do is:

`cp -r argon2 custom.cfg /boot/grub/`

GRUB2 should now be able to unlock LUKS2 Argon2id volumes (with `GRUB_ENABLE_CRYPTODISK=y` in `/etc/default/grub`).

The LUKS2 module with Argon2 support is loaded first in custom.cfg (which is automatically loaded by grub.cfg), preventing GRUB from loading the original LUKS2 module.

## Compile from source

- Clone the GRUB repository and apply the patches from the AUR package.
- In `grub-core/lib/argon2/argon2.c`, change the value of `GRUB_MOD_LICENSE` to `"GPLv3+"` so that it is accepted by the default GRUB module loader.
- Build GRUB and copy the modules `luks2.mod` and `argon2.mod` from the `grub-core` folder.

## Disclaimer

I tested it on Void Linux with GRUB 2.12 (EFI), but it should work on any distro with GRUB 2.12. It may or may not work on other GRUB2 versions. Use it at your own risk. I am not responsible for any issues, damage, or loss that may result from using these modules.
