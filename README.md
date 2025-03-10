# Debian DKMS package for ntsync kernel module

The [ntsync](https://lore.kernel.org/all/20241213193511.457338-1-zfigura@codeweavers.com/) driver implementing NT synchronization primitives was merged for Linux 6.14.
This repository contains the source of a Debian package that uses DKMS to automatically build and install the ntsync kernel modules on Debian Bookworm (Linux 6.1) and Trixie/Sid (Linux 6.12).
Although untested, it should also work on Debian derivates like Ubuntu.

Current ntsync version is [6.14-rc6](https://web.git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/drivers/misc/ntsync.c?h=v6.14-rc6)
from [mainline](https://web.git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/drivers/misc/ntsync.c).

Build and install the .deb package as follows:

```sh
sudo dpkg-deb -b ntsync-dkms.deb.d ntsync-dkms_6.14-rc6_all.deb
sudo apt install ./ntsync-dkms_6.14-rc6_all.deb
```
