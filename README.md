# Arch/Artix Linux installation guide with full disk encryption

## Pre-installation

### Download distribution image

First of all, let's download distribution image.

- #### Arch GNU/Linux

The .iso image can be downloaded on the [download page](https://archlinux.org/download/).

- #### Artix GNU/Linux

Artix GNU/Linux has more variations than Arch GNU/Linux. Artix GNU/Linux download page provides .iso images with various initialization systems (OpenRC, Dinit, Runit, S6, Suite66) and desktop environments (Cinnamon, LXDE, LXQT, MATE, KDE Plasma, XFCE).
In this guide, we will install Artix GNU/Linux with OpenRC and without desktop environment (base install).
The .iso image can be downloaded on the [download page](https://artixlinux.org/download.php).

### Verify integrity

To do this, we need to compare the hash sum of the distribution image with the hash sum provided on the download page.

- #### Arch GNU/Linux

The .iso image checksums are listed on the [download page](https://archlinux.org/download/).

![Checksums of Arch GNU/Linux image](./images/arch_linux_iso_checksums.png)

Checksums are also listed on the mirror sites listed on the [download page](https://archlinux.org/download/).

![Mirror list for Arch GNU/Linux image](./images/arch_linux_mirror_list.png)

For example, on this [mirror site](https://mirror.rackspace.com/archlinux/iso/2022.03.01/) , the checksums are in .txt files.

![Mirror site for Arch GNU/Linux](./images/arch_linux_mirror_site.png)

The content of the .txt file containing SHA-1 checksums:

![SHA-1 checksums for Arch GNU/Linux](./images/arch_linux_mirror_site_checksums.png)

To get the SHA-1 hash sum of the .iso image, we need to do the following:
```zsh
sha1sum path/to/arch/image
```

Example of the command result:

![Checksum of Arch GNU/Linux](./images/arch_linux_iso_checksum_result.png)

We see that the SHA-1 hash sums are equal.

- #### Artix GNU/Linux

The .iso image checksums are listed on the [download page](https://artixlinux.org/download.php).

![Checksums of Artix GNU/Linux image](./images/artix_linux_iso_checksums.png)

Checksums are also listed on the mirror sites listed on the [download page](https://artixlinux.org/download.php).

![Mirror list for Artix GNU/Linux](./images/artix_linux_mirror_list.png)

For example, on this [mirror site](https://mirrors.dotsrc.org/artix-linux/iso/) , the checksums are in sha256sums file.

![Mirror site for Artix GNU/Linux](./images/artix_linux_mirror_site.png)

The content of the sha256sums file containing SHA-256 checksums:

![SHA-256 checksums for Artix GNU/Linux](./images/artix_linux_mirror_site_checksums.png)

To get the SHA-256 hash sum of the .iso image, we need to do the following:
```zsh
sha256sum path/to/artix/image
```
Example of the command result:

![Checksum of Artix GNU/Linux](./images/artix_linux_iso_checksum_result.png)

We see that SHA-256 hash sums are equal.

### Verify signature

Let's download the GPG signature file corresponding to the distribution image we downloaded. And verify the .iso image.

- #### Arch GNU/Linux

To verify the Arch GNU/Linux image using GNU Privacy Guard, we need to do the following:
```zsh
gpg --keyserver-options auto-key-retrieve --verify archlinux-version-x86_64.iso.sig
```
After executing this command, you should see the following:

![GPG signature for Arch GNU/Linux image](./images/arch_linux_gpg_signature_checking.png)

This is a "Good signature", so everything is fine.

- #### Artix GNU/Linux

For Artix GNU/Linux, the command is similar:
```zsh
gpg --keyserver-options auto-key-retrieve --verify artix-base-openrc-version-x86_64.iso.sig
```

After executing this command, you should see the following:

![GPG signature for Artix GNU/Linux image](./images/artix_linux_gpg_signature_checking.png)

This is a "Good signature", so everything is fine.

### Creating a USB drive with a recorded distribution image

This will irrevocably destroy all data on you USB drive.
To find the name of your USB drive, you need to use `lsblk` command. Make sure that it is not mounted.

- #### On GNU/Linux

Using `dd` command:
```zsh
dd bs=4M if=path/to/distribution/image of=path/to/usb/drive
```

Using `cat` command:
```
cat path/to/distribution/image > path/to/usb/drive
```

Using `cp` command:
```zsh
cp path/to/distribution/image path/to/usb/drive
```

Using `tee` command:
```zsh
tee < path/to/distribution/image > path/to/usb/drive
```

Using `pv` command:
```zsh
pv path/to/distribution/image > path/to/usb/drive
```

All these commands are part of GNU core utilities.

- #### On Windows

You need to download some software to create bootable USB drives. For example: Rufus, Etcher.

### Boot the live environment

Arch GNU/Linux and Artix GNU/Linux installation images do not support Secure boot.
You will need to disable Secure boot to boot the installation medium.
If desired, Secure boot can be set up after completing the installation.

For this step, you need to restart your computer and enter the boot menu, then select your USB drive as the boot device (just change the boot priority).
Save the download settings and start your computer.

Congratulations, you have launched Arch/Artix Linux!

### Set the keyboard layout

To check the available layout types:
```zsh
ls -R /usr/share/kbd/keymaps/
```

To set the keyboard layout, pass a corresponding file name to loadkeys command, omitting path and file extension. 

For example, to set the Spanish (Spain) layout, type:
```zsh
loadkeys es
```

Console fonts are located in `/usr/share/kbd/consolefonts/` and can likewise be set with setfont command.
