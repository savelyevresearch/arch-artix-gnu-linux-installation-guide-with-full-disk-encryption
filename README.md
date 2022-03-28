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

![Mirror site for Artix GNU/Linux](./images/arch_linux_mirror_site.png)

The content of the sha256sums file containing SHA-256 checksums:

![SHA-256 checksums for Artix GNU/Linux](./images/artix_linux_mirror_site_checksums.png)

To get the SHA-256 hash sum of the .iso 0image, we need to do the following:
```zsh
sha256sum path/to/artix/image
```
Example of the command result:

![Checksum of Artix GNU/Linux](./images/artix_linux_iso_checksum_result.png)

We see that SHA-256 hash sums are equal.
